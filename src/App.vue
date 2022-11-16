<template>
  <div id="drawlayer">
    <div id="web3d" style="z-index: 1; height: 100%; width: 100%"></div>
  </div>
</template>

<script>
import * as webgz3d from "webgz3d";
export default {
  data() {
    return {};
  },
  mounted() {
    var webgz3dObj = new webgz3d.DevScene();
    webgz3dObj.gzwindowController.DoAsyncLoadBuilding().then(() => {
      webgz3dObj.gzwindowController.setBuildingNo(19);
      //webgz3dObj.gzwindowController.setSingleWindowVisibility("1东1-3", false);
      let eastList = webgz3dObj.gzwindowController.getDirectionWindow("东");
      let westList = webgz3dObj.gzwindowController.getDirectionWindow("西");
      let southList = webgz3dObj.gzwindowController.getDirectionWindow("南");
      let northList = webgz3dObj.gzwindowController.getDirectionWindow("北");

      let totalList = [];
      totalList.push(...eastList);
      totalList.push(...westList);
      totalList.push(...northList);
      totalList.push(...southList);

      console.log(totalList.find((e) => e == "19南1-5"));

      webgz3dObj.gzwindowController.setSingleWindowVisibility("19东25-1", true);
      webgz3dObj.gzwindowController.setBuildingNo(1);
      webgz3dObj.gzwindowController.setSingleWindowVisibility("1南1-1", true);
      //webgz3dObj.gzwindowController.setSingleWindowVisibility("1北13-3", true); //设置单个窗户显示或隐藏
      //webgz3dObj.gzwindowController.setAllWindowsVisible(); //设置全部窗户显示
    });

    webgz3d.EventBus.UIEvent.addListener("LoadWindowProcess", (e) => {
      //var p = { process: "测试数据" };
      //webgz3dObj.gzwindowController.showProcess(e, p);

      // let div = document.createElement("div");
      // div.innerText = "tewtewr";
      // div.style.background = "#fff";
      // div.style.width = "60px";
      // div.style.height = "40px";
      // div.style.zIndex = "10";
      // div.style.position = "absolute";
      // div.style.left =
      //   (e.canvasPosition.x / window.devicePixelRatio).toString() + "px";
      // div.style.top =
      //   (e.canvasPosition.y / window.devicePixelRatio).toString() + "px";
      // document.documentElement.appendChild(div);

      console.log(e);
      console.log(e.canvasPosition.x / window.devicePixelRatio);
      console.log(e.canvasPosition.y / window.devicePixelRatio);
    });
  },
};
</script>

<style></style>
