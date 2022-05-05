# finish
# finish

#### 介绍
以下是 Three.js实现跳一跳


#### 教程
 

```
 //1.场景
  let scene=new THREE.Scene();
  //创建一个场景
  //2.相机
  let camera=new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,1,1000);
  //创建一个透视相机 4个参数（视觉范围，宽高比例，距离，远距离）
  camera.position.z=10;
  //z轴 距离越远看到的越小
  camera.position.y=3;
  //y轴 上
  camera.position.x=8;
  //x轴 右
  
  //3.几何体
  let geometry=new THREE.CubeGeometry(4,2,4);
  //创建一个几何体对象 （宽，高，深度）
  let material=new THREE.MeshLambertMaterial({color:0xbebebe});
  //创建了一个可以用于立方体的材质,对象包含了颜色、透明度等属性，
  let cube=new THREE.Mesh(geometry,material);
  //结合在一起
  cube.position.x=16;
  scene.add(cube);
  //添加到场景中
  
  //光照
  let directionalLight=new THREE.DirectionalLight(0xffffff,1.1);
  //平行光  （颜色，强度)
  directionalLight.position.set(3,10,5);
  //平行光位置
  scene.add(directionalLight);
  //在场景中加入平行光
  let light=new THREE.AmbientLight(0xffffff,0.4);
  //光的材质
  scene.add(light);
  //4.渲染器
  let renderer=new THREE.WebGLRenderer({antialias:true});
  //创建一个渲染器 （让边缘动画没有锯齿感）
  renderer.setSize(window.innerWidth,window.innerHeight);
  // 画布宽高
  renderer.setClearColor(0x282828);
  //修改画布颜色
  renderer.render(scene,camera);
  //渲染场景相机 （后续更新也是这里）
  document.body.appendChild(renderer.domElement);
  //把当前渲染的画布放到body里面
  let x=8;
  function render() {
	  //递归
    x-=0.1;
    camera.position.x=x;
    renderer.render(scene,camera);
	//更新重新渲染
    if(x>=-8){
	//满足当前条件
      requestAnimationFrame(render)
	  //循环渲染
    }
  }
  //render();
```


#### 使用说明

下载点击HTML文件即可


