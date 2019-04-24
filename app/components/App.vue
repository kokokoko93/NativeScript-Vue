<template>
    <Page>
        <ActionBar>
            <GridLayout width="100%" columns="auto, *">
                <Label text="MENU" @tap="$refs.drawer.nativeView.showDrawer()" col="0"/>
                <Label class="title" text="Welcome to NativeScript-Vue!"  col="1"/>
            </GridLayout>
            <NavigationButton visibility="never" android.systemIcon="ic_menu_back" />
        </ActionBar>

        <RadSideDrawer ref="drawer">
            <StackLayout ~drawerContent backgroundColor="#ffffff">
                <Label class="drawer-header" text="Drawer"/>

                <Label class="drawer-item" text="Item 1"/>
                <Label @tap="$navigateTo(Item2Page)" class="drawer-item" text="Item 2"/>
                <Label class="drawer-item" text="Item 3"/>
            </StackLayout>

            <GridLayout ~mainContent columns="*" rows="*">
                <!-- <Label class="message" :text="msg" col="0" row="0"/> -->
                <Image
                    :imageSource="imageSource"
                />
            </GridLayout>
        </RadSideDrawer>
    </Page>
</template>

<script >
    import Item2 from '@/components/Item2'
    import { fromNativeSource } from 'tns-core-modules/image-source'
    import ZXing from 'nativescript-zxing'
    export default {
        data() {
            return {
                msg: '一起同步測試看看模擬器給不給力!',
                Item2Page: Item2,
                imageSource: null
            };
        },
        beforeMount() {
            const zx = new ZXing()
            const barcode = zx.createBarcode({ encode: 'AZ000001', height: 200, width: 200, format: ZXing.QR_CODE })
            this.imageSource = fromNativeSource(barcode)
        }
    }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .title {
        text-align: left;
        padding-left: 16;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    .drawer-header {
        padding: 50 16 16 16;
        margin-bottom: 16;
        background-color: #53ba82;
        color: #ffffff;
        font-size: 24;
    }

    .drawer-item {
        padding: 8 16;
        color: #333333;
        font-size: 30;
    }
</style>
