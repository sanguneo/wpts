---
contentLayout: DocsWrapper
versionInfo: 0.16.5
---

# API Reference

## Namespaces
    
<br>

#### Crane : <code>object</code>
> Crane

**Version**: 0.16.5  
**Author**: gyu@urbanbase.com  

* * *


<br>

##### Crane.init(options)
> 기본적인 설정 값을 주입힌다


| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> |  |
| options.apiKEY | <code>string</code> | // 필수 값: UB로 부터 부여받은 api key |
| options.companyCODE | <code>string</code> |  |
| options.baseURL | <code>string</code> | // 실제 데이터 통신을 위한 API: 없을 경우 내부 API 호출 |
| options.cfURL | <code>string</code> | // CDN 주소 (3D모델 파일, 이미지) : 없을 경우 내부 CDN 호출 |
| options.endPoint | <code>string</code> | // baseURL 뒤에 붙는 api end point (ex: company, admin, me) |
| options.pathData | <code>Object</code> | // posts, assets, units, materials 조회시 쓰이는 path를 별도로 지정 |

**Example**  
```javascript
// 하위 예제는 파라미터 형식을 보여주기 위한 값들로 실제 동작 안함
// 최초 생성시 Crane.init() 필수
// custom URL 사용시 :  baseURL + pathData,  baseURL + endPoint + pathData 사용
Crane.init({
  apiKEY: 'keycodeexampleaaaabbbbcccc123',
  companyCODE: 'companycode123',
  cfURL: 'https://www.cdn.com/',
  baseURL: 'https://api.example.com/v3',
  endPoint: 'company',
  pathData: { posts: 'posts', assets: 'assets', units: 'units', materials: 'materials' },
});
```
**Example**  
```javascript
// ex1) get post api url : https://www.api.kr/myposts/{id}
Crane.init({
  baseURL: 'https://www.api.kr/',
  pathData: { posts: 'myPosts' }
});
```
**Example**  
```javascript
// ex2) get post api url : https://www.api.kr/my/privatePosts/{id}
 Crane.init({
   baseURL: 'https://www.api.kr/',
   endPoint: 'my',
   pathData: { posts: 'privatePosts' }
});
```

* * *


## Modules
<dl>
    <dt><a href="#module_Player">Player</a></dt><dd><p>3D 화면에 대한 객체 (하위에 Camera, Light, History, Setting 객체를 지님)</p>
</dd>
</dl><dl>
    <dt><a href="#module_Product">Product</a></dt><dd><p>상품에 대한 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_ProductModel">ProductModel</a></dt><dd><p>상품과 메타 정보에 대한 모델 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Structure">Structure</a></dt><dd><p>도면에 대한 객체 (하위에 Ruler, Paint 객체를 지님)</p>
</dd>
</dl><dl>
    <dt><a href="#module_StructureModel">StructureModel</a></dt><dd><p>건축물에 정보에 대한 모델 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Custom">Custom</a></dt><dd><p>Custom에 대한 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_ProductStructure">ProductStructure</a></dt><dd><p>구조설비 상품에 대한 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Post">Post</a></dt><dd><p>홈 디자이닝 데이터를 로드하는 객체 ( 도면, 제품들의 데이터를 로드 )</p>
</dd>
</dl><dl>
    <dt><a href="#module_PostModel">PostModel</a></dt><dd><p>홈디자이닝 데이터에 대한 API</p>
</dd>
</dl><dl>
    <dt><a href="#module_Camera">Camera</a></dt><dd><p>카메라의 설정에 대한 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Light">Light</a></dt><dd><p>빛 설정에 대한 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Paint">Paint</a></dt><dd><p>벽지/바닥재의 스타일을 변경하는 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Ruler">Ruler</a></dt><dd><p>길이/면적을 재는 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Setting">Setting</a></dt><dd><p>플레이어의 기본 설정에 대한 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_History">History</a></dt><dd><p>히스토리를 관리하는 객체</p>
</dd>
</dl><dl>
    <dt><a href="#module_Renderer">Renderer</a> ⇐ <code>EventEmitter</code></dt><dd><p>unity 화면을 렌더링하는 객체</p>
</dd>
</dl>
<br>

#### Player
> 3D 화면에 대한 객체 (하위에 Camera, Light, History, Setting 객체를 지님)


| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> |  |
| mode | <code>string</code> | 'Template' || 'HomeDesign' || 'ProductView' || 'HomeView' |

**Example**  
```javascript
const player = new Crane.Player( 'viewer', 'ProductView' );
```

* [Player](#module_Player)
    * [.getCoreEid()](#module_Player+getCoreEid) ⇒ <code>string</code>
    * [.getEid()](#module_Player+getEid) ⇒ <code>number</code>
    * [.getId()](#module_Player+getId) ⇒ <code>string</code>
    * [.getStructure()](#module_Player+getStructure) ⇒ <code>Object</code>
    * [.getProducts()](#module_Player+getProducts) ⇒ <code>array</code>
    * [.getLastProduct()](#module_Player+getLastProduct) ⇒ <code>Object</code>
    * [.getCustoms()](#module_Player+getCustoms) ⇒ <code>array</code>
    * [.getLastCustom()](#module_Player+getLastCustom) ⇒ <code>Object</code>
    * [.getProductStructures()](#module_Player+getProductStructures) ⇒ <code>array</code>
    * [.cleanObject()](#module_Player+cleanObject)
    * [.setCDNPath()](#module_Player+setCDNPath)
    * [.setSDKMode(mode)](#module_Player+setSDKMode)
    * [.setOrbit()](#module_Player+setOrbit)
    * [.setFirstPerson()](#module_Player+setFirstPerson)
    * [.setPersonHeight(personHeight)](#module_Player+setPersonHeight)
    * [.setFieldOfView(fov)](#module_Player+setFieldOfView)
    * [.setPositionOfCamera(presetView)](#module_Player+setPositionOfCamera)
    * [.set2D()](#module_Player+set2D)
    * [.set3D()](#module_Player+set3D)
    * [.enableCameraRotation()](#module_Player+enableCameraRotation)
    * [.disableCameraRotation()](#module_Player+disableCameraRotation)
    * [.enableCameraPanning()](#module_Player+enableCameraPanning)
    * [.disableCameraPanning()](#module_Player+disableCameraPanning)
    * [.setScreenResolution(width, height)](#module_Player+setScreenResolution)
    * [.setScreenQuality(quality)](#module_Player+setScreenQuality)
    * [.screenShot(hasBackground)](#module_Player+screenShot)
    * [.setShadowType(shadowType)](#module_Player+setShadowType)
    * [.setVSync(vsync)](#module_Player+setVSync)
    * [.setBackgroundColor(bgColor)](#module_Player+setBackgroundColor)
    * [.setBrightnessToMonthAndHour(monthAndHour)](#module_Player+setBrightnessToMonthAndHour)
    * [.turnOnProductCollisionAvoidance()](#module_Player+turnOnProductCollisionAvoidance)
    * [.turnOffProductCollisionAvoidance()](#module_Player+turnOffProductCollisionAvoidance)
    * [.turnOnProductFreeMovement()](#module_Player+turnOnProductFreeMovement)
    * [.turnOffProductFreeMovement()](#module_Player+turnOffProductFreeMovement)
    * [.turnOnGrid()](#module_Player+turnOnGrid)
    * [.turnOffGrid()](#module_Player+turnOffGrid)
    * [.undo()](#module_Player+undo)
    * [.redo()](#module_Player+redo)
    * [.abledToUndo()](#module_Player+abledToUndo)
    * [.abledToRedo()](#module_Player+abledToRedo)
    * [.clearHistory()](#module_Player+clearHistory)
    * [.pause()](#module_Player+pause)
    * [.resume()](#module_Player+resume)
    * [.load(obj)](#module_Player+load)
    * [.loadFromFile(product)](#module_Player+loadFromFile)
    * [.isOrthographic()](#module_Player+isOrthographic) ⇒ <code>boolean</code>
    * [.isPerspective()](#module_Player+isPerspective) ⇒ <code>boolean</code>
    * [.isOrbit()](#module_Player+isOrbit) ⇒ <code>boolean</code>
    * [.isFirstPerson()](#module_Player+isFirstPerson) ⇒ <code>boolean</code>
    * [.getProductsCount()](#module_Player+getProductsCount) ⇒ <code>number</code>
    * [.getCustomsCount()](#module_Player+getCustomsCount) ⇒ <code>number</code>
    * [.getProductStructuresCount()](#module_Player+getProductStructuresCount) ⇒ <code>number</code>
    * [.changeProductStructure(data)](#module_Player+changeProductStructure)


* * *

##### getCoreEid()
> Core eid를 리턴한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>string</code>
* * *

##### getEid()
> Event id를 리턴한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>number</code>
* * *

##### getId()
> Element ID를 리턴한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>string</code>
* * *

##### getStructure()
> 도면을 리턴한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>Object</code>
* * *

##### getProducts()
> 제품 리스트를 리턴한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>array</code>
* * *

##### getLastProduct()
> 맨마지막 제품을 리턴한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>Object</code>
* * *

##### getCustoms()
> 커스텀 제품 리스트를 리턴한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>array</code>
* * *

##### getLastCustom()
> 마지막 커스텀 제품을 리턴한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>Object</code>
* * *

##### getProductStructures()
> 구조설비 제품 리스트를 리턴한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>array</code>
* * *

##### cleanObject()
> 모든 제품들을 제거한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### setCDNPath()
> CDN Path를 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### setSDKMode(mode)
> SDK 모드를 변경한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| mode | <code>string</code> | 'Template' || 'HomeDesign' || 'ProductView' || 'HomeView' |


* * *

##### setOrbit()
> 카메라를 Orbit으로 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### setFirstPerson()
> 카메라를 First Person으로 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### setPersonHeight(personHeight)
> First Person 모드 일 때, 사람의 높이를 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type |
| --- | --- |
| personHeight | <code>number</code> | 


* * *

##### setFieldOfView(fov)
> 카메라의 시야각을 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| fov | <code>number</code> | 10 ~ 160 |

**Example**  
```javascript
//angle of view : Low
player.setFieldOfView(40);

// angle of view : Normal
player.setFieldOfView(60);

// angle of view : Wide
player.setFieldOfView(80);
```

* * *

##### setPositionOfCamera(presetView)
> 플레이어의 카메라 위치를 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| presetView | <code>Object</code> | { euler_angle: {pitch, yaw, roll}, distance: distance, isOrtho: false, target_position: []} |

**Example**  
```javascript
const presetView = {
        euler_angle : {
            pitch : (float) // -90 ~ 90
            yaw : (float) // 0 ~ 360
            roll: (float) // 0 ~ 360
        },
        // 선택사항 1
        distance : (float),

        // 선택사항 2
        target_position : (float_array / length 3),

        // 선택사항 3
        isOrtho : (bool) // 기본값 false
    }

   player.setPositionOfCamera(presetView);
```

* * *

##### set2D()
> 2D view로 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Example**  
```javascript
// 2D 모드
player.set2D();
```

* * *

##### set3D()
> 3D view로 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Example**  
```javascript
// 3D 모드
player.set3D();
```

* * *

##### enableCameraRotation()
> 카메라의 회전을 활성화 시킨다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### disableCameraRotation()
> 카메라의 회전을 비활성화 시킨다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### enableCameraPanning()
> 카메라의 panning을 활성화 시킨다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### disableCameraPanning()
> 카메라의 panning을 비활성화 시킨다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### setScreenResolution(width, height)
> 스크린의 사이즈를 조절한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type |
| --- | --- |
| width | <code>number</code> | 
| height | <code>number</code> | 


* * *

##### setScreenQuality(quality)
> 스크린의 해상도를 조절한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| quality | <code>number</code> | 0 -> 저해상도 | 1 -> 평해상도(중간) | 2 -> 고해상도 |

**Example**  
```javascript
// 저해상도
player.setScreenQuality(0);

// 평해상도(중간)
player.setScreenQuality(1);

// 고해상도
player.setScreenQuality(2);
```

* * *

##### screenShot(hasBackground)
> 스크린 샷을 찍는다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type |
| --- | --- |
| hasBackground | <code>boolean</code> | 


* * *

##### setShadowType(shadowType)
> 그림자의 형태를 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| shadowType | <code>string</code> | 'none'|'hard'|'soft' |


* * *

##### setVSync(vsync)
> Vsync를 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type |
| --- | --- |
| vsync | <code>number</code> | 


* * *

##### setBackgroundColor(bgColor)
> 플레이어의 백그라운드 컬러를 설정한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type |
| --- | --- |
| bgColor | <code>object</code> | 

**Example**  
```javascript
const black = {
        color_top: {
          r: 18, g: 34, b: 45, a: 1,
        },
        color_bottom: {
          r: 36, g: 59, b: 80, a: 1,
        }
   };
   const gray = {
    color_top: {
      r: 172, g: 172, b: 172, a: 1,
    },
    color_bottom: {
      r: 255, g: 255, b: 255, a: 1,
    },
  };

   // 검정 배경
   player.setBackgroundColor(black);

   // 회색 배경
   player.setBackgroundColor(gray);
```

* * *

##### setBrightnessToMonthAndHour(monthAndHour)
> 월과 시간을 설정하여 빛의 세기를 조절한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| monthAndHour | <code>Object</code> | {month: 1 ~ 12 , hour: 0 ~ 24 } |

**Example**  
```javascript
player.setBrightnessToMonthAndHour({month: 5, hour: 14});
```

* * *

##### turnOnProductCollisionAvoidance()
> 상품의 충돌 방지를 켠다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### turnOffProductCollisionAvoidance()
> 상품의 충돌 방지를 끈다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### turnOnProductFreeMovement()
> 상품의 자유 이동 기능을 켠다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### turnOffProductFreeMovement()
> 상품의 자유 이동 기능을 끈다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### turnOnGrid()
> 그리드를 켠다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### turnOffGrid()
> 그리드를 끈다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### undo()
> 이전 상태로 되돌린다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### redo()
> 이후 상태로 되돌린다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### abledToUndo()
> 이전 상태로 되돌리기가 가능한지 확인한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### abledToRedo()
> 이후 상태로 되돌리기가 가능한지 확인한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### clearHistory()
> 모든 히스토리를 초기화한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### pause()
> Player를 일시 정지 한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### resume()
> Player를 다시 시작한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  

* * *

##### load(obj)
> 플레이어 위에 객체를 로드한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>object</code> | Structure, Product, Custom, ProductStructure, Post |

**Example**  
```javascript
const structure = new Crane.Structure({
            id: id,
            url: 'signed_url' || null,
            format: 'dae',
      });
player.load(structure);

const product = new Crane.Product({ id: 'assetId', assetUuid: 'assetUuid'});
player.load(product);

const custom = new Crane.Custom({
        type: 'box' || 'desk',
        width: 1000,
        height: 1000,
        depth: 1000,
      });
player.load(custom);
```

* * *

##### loadFromFile(product)
> 파일의 path를 통해 로드시킨다

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type |
| --- | --- |
| product | <code>object</code> | 


* * *

##### isOrthographic()
> 직교투영 모드 여부 확인

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>boolean</code>
* * *

##### isPerspective()
> 원근법 모드 여부 확인

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>boolean</code>
* * *

##### isOrbit()
> observer 모드 인지 확인

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>boolean</code>
* * *

##### isFirstPerson()
> 1인칭 모드인지 확인

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>boolean</code>
* * *

##### getProductsCount()
> 제품의 총 수량을 리턴한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>number</code>
* * *

##### getCustomsCount()
> 커스텀 제품의 총 수량을 리턴한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>number</code>
* * *

##### getProductStructuresCount()
> 구조설비 제품의 총 수량을 리턴한다

**Kind**: instance method of [<code>Player</code>](#module_Player)  
**Returns**: <code>number</code>
* * *

##### changeProductStructure(data)
> 문/창 을 다른 문/창 제품으로 교체한다.

**Kind**: instance method of [<code>Player</code>](#module_Player)  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>object</code> | { type: '', assetUuid: '', assetId: '', format: '', style: '', origin_uuid: '' } |


* * *


<br>

#### Product
> 상품에 대한 객체


| Param | Type | Description |
| --- | --- | --- |
| params | <code>object</code> | 필수: 상품에 대한 정보들을 주입 (예제 참고) |
| token | <code>string</code> |  |
| errorCallback | <code>function</code> |  |

**Example**  
```javascript
// 객체 생성을 하면 GET API 요청시, request parameters 가 포함되어 전송됩니다.
// UB 내부에서 사용되는 예약어일 뿐이므로 걱정하지 마십시오.

// 응답 Data example :
// Product → https://wsdk.urbanbase.com/crane_js/sample/assets/1

const product = new Crane.Product( {
       assetUuid: '', // 필수: asset uuid
       id: '',
       url: '',
       format: '',
       style: {},
});
```

* [Product](#module_Product)
    * [.injectedRenderer(renderer)](#module_Product+injectedRenderer)
    * [.getEid()](#module_Product+getEid) ⇒ <code>number</code>
    * [.getId()](#module_Product+getId) ⇒ <code>\*</code>
    * [.setUuid(uuid)](#module_Product+setUuid)
    * [.getUuid()](#module_Product+getUuid) ⇒ <code>null</code>
    * [.setStyleId(styleId)](#module_Product+setStyleId)
    * [.getStyleId()](#module_Product+getStyleId) ⇒ <code>\*</code>
    * [.setTransform(transform)](#module_Product+setTransform)
    * [.getTransform()](#module_Product+getTransform) ⇒ <code>Object</code>
    * [.getDataToInject()](#module_Product+getDataToInject) ⇒ <code>Object</code>
    * [.select()](#module_Product+select)
    * [.deselect()](#module_Product+deselect)
    * [.remove()](#module_Product+remove)
    * [.copy()](#module_Product+copy)
    * [.flipVertical()](#module_Product+flipVertical)
    * [.flipHorizontal()](#module_Product+flipHorizontal)
    * [.setStyling(geometry, material)](#module_Product+setStyling)
    * [.setStyle(style)](#module_Product+setStyle)
    * [.setDefaultStyle()](#module_Product+setDefaultStyle)
    * [.getStyle()](#module_Product+getStyle) ⇒ <code>\*</code>
    * [.setSize(size)](#module_Product+setSize)
    * [.settingRealSize(size)](#module_Product+settingRealSize)
    * [.getSize()](#module_Product+getSize) ⇒ <code>Object</code>
    * [.setRise(rise)](#module_Product+setRise)
    * [.getRise()](#module_Product+getRise) ⇒ <code>number</code>
    * [.setGeometryStyles()](#module_Product+setGeometryStyles)
    * [.getGeometryData()](#module_Product+getGeometryData) ⇒ <code>\*</code>
    * [.setGeometryMaterialId(material_id)](#module_Product+setGeometryMaterialId)
    * [.getGeometryMaterialIds()](#module_Product+getGeometryMaterialIds) ⇒ <code>Array</code>
    * [.getOriginGeometryMaterialIds()](#module_Product+getOriginGeometryMaterialIds) ⇒ <code>Array</code>
    * [.getDefaultGeometryStyle()](#module_Product+getDefaultGeometryStyle) ⇒ <code>object</code>
    * [.changeDefaultStyle()](#module_Product+changeDefaultStyle)
    * [.resetGeometryMaterialIds()](#module_Product+resetGeometryMaterialIds)
    * [.setOriginalSize(size)](#module_Product+setOriginalSize)
    * [.getOriginalSize()](#module_Product+getOriginalSize) ⇒ <code>Object</code>
    * [.getStyles()](#module_Product+getStyles) ⇒ <code>\*</code>
    * [.getFormat()](#module_Product+getFormat) ⇒ <code>\*</code>
    * [.getPlaneType()](#module_Product+getPlaneType) ⇒ <code>\*</code>
    * [.getAssetStyleId()](#module_Product+getAssetStyleId) ⇒ <code>\*</code>


* * *

##### injectedRenderer(renderer)
> 렌더러가 주입되다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param |
| --- |
| renderer | 


* * *

##### getEid()
> Event id를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>number</code>
* * *

##### getId()
> id를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### setUuid(uuid)
> uuid를 저장한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| uuid | <code>string</code> | 


* * *

##### getUuid()
> uuid를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>null</code>
* * *

##### setStyleId(styleId)
> style id를 저장한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| styleId | <code>string</code> | 


* * *

##### getStyleId()
> style id를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### setTransform(transform)
> Transform 정보를 저장한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| transform | <code>object</code> | 

**Example**  
```javascript
const transform = {
    position: [0, 0, 0],
    rotation: [0, 0, 0],
    scale: [0, 0, 0],
}

product.setTransform(transform);
```

* * *

##### getTransform()
> Transform 정보를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>Object</code>
* * *

##### getDataToInject()
> 3D에 주입할 데이터를 전달한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>Object</code>
* * *

##### select()
> 화면에 존재하는 상품을 선택한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### deselect()
> 선택한 상품을 해제한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### remove()
> 상품을 삭제한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### copy()
> 상품을 복제한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### flipVertical()
> 상품을 수직으로 뒤집는다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### flipHorizontal()
> 상품을 수평으로 뒤집는다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### setStyling(geometry, material)
> Product에 geometry, material style을 입힌다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| geometry | <code>object</code> | 
| material | <code>object</code> | 

**Example**  
```javascript
product.setStyling(geometry, material);
```

* * *

##### setStyle(style)
> Product에 Style을 적용한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| style | <code>object</code> | 


* * *

##### setDefaultStyle()
> 기본 스타일 값을 설정한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### getStyle()
> 스타일 정보를 리턴한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### setSize(size)
> 사이즈를 다시 설정한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| size | <code>object</code> | 

**Example**  
```javascript
const size = {
    width: 0,
    height: 0,
    depth: 0,
    rise: 0,
}

product.setSize(size)
```

* * *

##### settingRealSize(size)
> size를 mm단위로 설정한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| size | <code>array</code> | 

**Example**  
```javascript
const size = [1, 1, 1];

product.settingRealSize(size);
```

* * *

##### getSize()
> 현재 사이즈를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>Object</code>
* * *

##### setRise(rise)
> 제품의 높이 값을 설정

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| rise | <code>number</code> | 


* * *

##### getRise()
> rise 값을 리턴한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>number</code>
* * *

##### setGeometryStyles()
> 지오메트리 매터리얼에 대한 정리를 한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### getGeometryData()
> 지오메터리 데이터를 리턴한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### setGeometryMaterialId(material_id)
> 지오메트리 매터리얼 id를 설정한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| material_id | <code>string</code> | 


* * *

##### getGeometryMaterialIds()
> 현재 지오메트리 id 리스트를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>Array</code>
* * *

##### getOriginGeometryMaterialIds()
> 기존 지오메트리 id 리스트를 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>Array</code>
* * *

##### getDefaultGeometryStyle()
> DefaultGeometryStyle을 리턴한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>object</code>
* * *

##### changeDefaultStyle()
> 기존 스타일로 변경한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### resetGeometryMaterialIds()
> 지오메트리 매터리얼 리스트를 초기화한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  

* * *

##### setOriginalSize(size)
> 기본 사이즈를 설정한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  

| Param | Type |
| --- | --- |
| size | <code>array</code> | 

**Example**  
```javascript
const size = [1,1,1]
product.setOriginalSize(size);
```

* * *

##### getOriginalSize()
> 기본 사이즈를 반환한다.

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>Object</code>
* * *

##### getStyles()
> 스타일 리스트를 반환한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### getFormat()
> format을 반환한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### getPlaneType()
> planeType 을 반환한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *

##### getAssetStyleId()
> assetStyleId을 반환한다

**Kind**: instance method of [<code>Product</code>](#module_Product)  
**Returns**: <code>\*</code>
* * *


<br>

#### ProductModel
> 상품과 메타 정보에 대한 모델 객체


* * *

##### getData(id)
> product의 데이터를 가져온다

**Kind**: instance method of [<code>ProductModel</code>](#module_ProductModel)  
**Returns**: <code>Promise.&lt;\*&gt;</code>
| Param |
| --- |
| id | 


* * *


<br>

#### Structure
> 도면에 대한 객체 (하위에 Ruler, Paint 객체를 지님)

**Example**  
```javascript
// 객체 생성을 하면 GET API 요청시, request parameters 가 포함되어 전송됩니다.
// UB 내부에서 사용되는 예약어일 뿐이므로 걱정하지 마십시오.

// 응답 Data example :
// Structure → https://wsdk.urbanbase.com/crane_js/sample/units/1

 const unit = new Crane.Structure({
          uuid: '', // 필수: 도면의 uuid
          id: '',
          url: '',
          public: true, // true | false
    });
```

* [Structure](#module_Structure)
    * [.injectedRenderer(renderer)](#module_Structure+injectedRenderer)
    * [.getDataToInject()](#module_Structure+getDataToInject) ⇒ <code>Object</code>
    * [.getEid()](#module_Structure+getEid) ⇒ <code>number</code>
    * [.getId()](#module_Structure+getId) ⇒ <code>\*</code>
    * [.getTransform()](#module_Structure+getTransform) ⇒ <code>Object</code>
    * [.setMaterials(material)](#module_Structure+setMaterials)
    * [.getMaterials()](#module_Structure+getMaterials) ⇒ <code>null</code> \| <code>Array</code> \| <code>\*</code>
    * [.setTransform(transform)](#module_Structure+setTransform)
    * [.checkData()](#module_Structure+checkData) ⇒ <code>Promise.&lt;\*&gt;</code>
    * [.changeStyleOfTarget()](#module_Structure+changeStyleOfTarget)
    * [.remove()](#module_Structure+remove)
    * [.flipHorizontal()](#module_Structure+flipHorizontal)
    * [.flipVertical()](#module_Structure+flipVertical)
    * [.setWallOpacity()](#module_Structure+setWallOpacity)
    * [.changeStyleOfFloor(materialId)](#module_Structure+changeStyleOfFloor)
    * [.changeStyleOfWall(materialId)](#module_Structure+changeStyleOfWall)
    * [.changeStyle(materialId)](#module_Structure+changeStyle)
    * [.stopToChangeStyle()](#module_Structure+stopToChangeStyle)
    * [.startMeasuringDistance()](#module_Structure+startMeasuringDistance)
    * [.endMeasuringDistance()](#module_Structure+endMeasuringDistance)
    * [.startMeasuringArea()](#module_Structure+startMeasuringArea)
    * [.endMeasuringArea()](#module_Structure+endMeasuringArea)
    * [.startFindCeiling()](#module_Structure+startFindCeiling)
    * [.stopFindCeiling()](#module_Structure+stopFindCeiling)
    * [.changeCeilingHeight(data)](#module_Structure+changeCeilingHeight)
    * [.setCeilingHeight(heightData)](#module_Structure+setCeilingHeight)
    * [.startFindFloor()](#module_Structure+startFindFloor)
    * [.stopFindFloor()](#module_Structure+stopFindFloor)
    * [.changeFloorHeight(data)](#module_Structure+changeFloorHeight)
    * [.setFloorHeight(floorData)](#module_Structure+setFloorHeight)
    * [.setDrawSliceFloor(data)](#module_Structure+setDrawSliceFloor)
    * [.removeDrawSliceFloor()](#module_Structure+removeDrawSliceFloor)
    * [.sliceFloor(data)](#module_Structure+sliceFloor)
    * [.setSliceData(floorData)](#module_Structure+setSliceData)
    * [.getFloorSplits()](#module_Structure+getFloorSplits) ⇒
    * [.changeDivisionFloors()](#module_Structure+changeDivisionFloors)
    * [.reMergeFloor(data)](#module_Structure+reMergeFloor)
    * [.deleteFloorSlice(floorData)](#module_Structure+deleteFloorSlice)
    * [.deleteMaterials(floorData)](#module_Structure+deleteMaterials)


* * *

##### injectedRenderer(renderer)
> 렌더러가 주입되다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param |
| --- |
| renderer | 


* * *

##### getDataToInject()
> 3D에 주입할 데이터를 전달한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: <code>Object</code>
* * *

##### getEid()
> Event id를 리턴한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: <code>number</code>
* * *

##### getId()
> id를 리턴한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: <code>\*</code>
* * *

##### getTransform()
> Transform 정보를 리턴한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: <code>Object</code>
* * *

##### setMaterials(material)
> material 속성을 저장한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| material | <code>object</code> | 

**Example**  
```javascript
structure.setMaterials({
   index: 0,
   material_id: '',
   unit_layer: 'RMF' || 'CIL',
   height: 0.5,
   angle: 30,
});
```

* * *

##### getMaterials()
> material들의 속성을 리턴한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: <code>null</code> \| <code>Array</code> \| <code>\*</code>
* * *

##### setTransform(transform)
> Transform 정보를 저장한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param |
| --- |
| transform | 


* * *

##### checkData()
> 값의 존재 유무를 확인한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: <code>Promise.&lt;\*&gt;</code>
* * *

##### changeStyleOfTarget()
> 저장된 Material을 적용한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### remove()
> 건축물을 제거

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### flipHorizontal()
> 건축물 수평 반전

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### flipVertical()
> 건축물 수직 반전

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### setWallOpacity()
> 벽투명도를 조절한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### changeStyleOfFloor(materialId)
> 바닥재의 스타일을 변경한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| materialId | <code>string</code> | 


* * *

##### changeStyleOfWall(materialId)
> 벽지의 스타일을 변경한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| materialId | <code>string</code> | 


* * *

##### changeStyle(materialId)
> 바닥재와 벽지의 스타일을 변경한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| materialId | <code>string</code> | 


* * *

##### stopToChangeStyle()
> 바닥재 또는 벽지의 스타일 변경 모드를 취소한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### startMeasuringDistance()
> 바닥의 거리 측정을 시작한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### endMeasuringDistance()
> 바닥의 거리 측정을 종료한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### startMeasuringArea()
> 바닥의 면적 측정을 시작한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### endMeasuringArea()
> 바닥의 면적 측정을 종료한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### startFindCeiling()
> 천장을 탐색하는 이벤트를 실행한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### stopFindCeiling()
> 천장을 탐색하는 이벤트를 중단한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### changeCeilingHeight(data)
> 천장 높이를 변경한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| data | <code>object</code> | 

**Example**  
```javascript
const data = {
        index: 0,
        height: 1.1,
      };

      structure.changeCeilingHeight(data);
```

* * *

##### setCeilingHeight(heightData)
> 천장 높이를 변경 결과를 변수에 저장한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| heightData | <code>object</code> | 

**Example**  
```javascript
structure.setCeilingHeight({
   unit_layer: 'CIL',
   index: 0,
   height: 1.1,
});
```

* * *

##### startFindFloor()
> 바닥을 탐색하는 이벤트를 실행한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### stopFindFloor()
> 바닥을 탐색하는 이벤트를 중단한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### changeFloorHeight(data)
> 바닥의 높이를 변경한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| data | <code>object</code> | 

**Example**  
```javascript
const data = {
    unit_layer: 'RMF',
    index: 0,
    height: 0.5
}
structure.changeCeilingHeight(data);
```

* * *

##### setFloorHeight(floorData)
> 바닥 높이를 변수에 저장한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| floorData | <code>object</code> | 

**Example**  
```javascript
structure.setFloorHeight({
   unit_layer: 'RMF',
   index: 0,
   height: 0.5,
});
```

* * *

##### setDrawSliceFloor(data)
> 방분할 임시선을 그린다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| data | <code>object</code> | 

**Example**  
```javascript
const data = {
      unit_layer: 'RMF',
      index: 0,
      type: 'line' || 'rect',
      angle: 0, // 0 ~ 360
      size: [1, 1] // [width 값, height 값] type == 'rect' 일 때만 유효
    }

   structure.setDrawSliceFloor(data);
```

* * *

##### removeDrawSliceFloor()
> 방문할을 위한 임시선을 제거한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### sliceFloor(data)
> 방분할을 한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| data | <code>object</code> | 

**Example**  
```javascript
const data = {
      unit_layer: 'RMF',
      index: 3,
      type: 'line' || 'rect',
      position: [3.476, 0, -3.522],
      angle: 0, // 0 ~ 360
      size: [0.5, 1] // [width 값, height 값] type == 'rect' 일 때만 유효
    }

   structure.sliceFloor(data);
```

* * *

##### setSliceData(floorData)
> 분할된 방에 대한 정보를 저장한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| floorData | <code>object</code> | 

**Example**  
```javascript
structure.setSliceData({
angle: 0,
     index: 3,
     position: [3.476, 0, -3.522],
     size: [0.5, 1],
     unit_layer: "RMF",
   });
```

* * *

##### getFloorSplits()
> 방분할 정보를 반환한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  
**Returns**: []
* * *

##### changeDivisionFloors()
> 방분할 정보를 가지고 방을 분할한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

* * *

##### reMergeFloor(data)
> 분할된 방을 다시 되돌린다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param |
| --- |
| data | 

**Example**  
```javascript
structure.reMergeFloor({unit_layer: 'RMF', index: 0})
```

* * *

##### deleteFloorSlice(floorData)
> 분할 선을 제거한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param | Type |
| --- | --- |
| floorData | <code>object</code> | 

**Example**  
```javascript
const floorData = { index: 0 };

structure.deleteFloorSlice(floorData);
```

* * *

##### deleteMaterials(floorData)
> 분할된 바닥에 대한 materials 정보를 제거한다

**Kind**: instance method of [<code>Structure</code>](#module_Structure)  

| Param |
| --- |
| floorData | 

**Example**  
```javascript
const floorData = {
 index: 0
 new_indices: [3, 4],
 unit_layer: 'RMF'
}

structure.deleteMaterials(floorData);
```

* * *


<br>

#### StructureModel
> 건축물에 정보에 대한 모델 객체


* [StructureModel](#module_StructureModel)
    * [.getData(unitId)](#module_StructureModel+getData) ⇒ <code>Promise.&lt;(null\|boolean\|\*)&gt;</code>
    * [.getMaterial(id)](#module_StructureModel+getMaterial) ⇒ <code>Promise.&lt;\*&gt;</code>
    * [.getDefaultMaterials()](#module_StructureModel+getDefaultMaterials) ⇒ <code>Promise.&lt;(null\|Array)&gt;</code>


* * *

##### getData(unitId)
> 건축물의 SignedUrl 정보를 가져온다

**Kind**: instance method of [<code>StructureModel</code>](#module_StructureModel)  
**Returns**: <code>Promise.&lt;(null\|boolean\|\*)&gt;</code>
| Param |
| --- |
| unitId | 


* * *

##### getMaterial(id)
> 메터리얼 정보를 가져온다

**Kind**: instance method of [<code>StructureModel</code>](#module_StructureModel)  
**Returns**: <code>Promise.&lt;\*&gt;</code>
| Param |
| --- |
| id | 


* * *

##### getDefaultMaterials()
> 디폴트 메터리얼 정보를 가져온다

**Kind**: instance method of [<code>StructureModel</code>](#module_StructureModel)  
**Returns**: <code>Promise.&lt;(null\|Array)&gt;</code>
* * *


<br>

#### Custom
> Custom에 대한 객체

**Example**  
```javascript
const custom = new Crane.Custom({
          type: 'box', // 필수: 'box' | 'desk'
          width: 1000,
          height: 1000,
          depth: 1000,
          transform: {
            position: [0, 0, 0],
          },
      });
```

* [Custom](#module_Custom)
    * [.injectedRenderer(renderer)](#module_Custom+injectedRenderer)
    * [.getEid()](#module_Custom+getEid) ⇒ <code>number</code>
    * [.setUuid(uuid)](#module_Custom+setUuid)
    * [.getUuid()](#module_Custom+getUuid) ⇒ <code>null</code>
    * [.getType()](#module_Custom+getType) ⇒ <code>\*</code>
    * [.setSize(size)](#module_Custom+setSize)
    * [.getSize()](#module_Custom+getSize) ⇒ <code>Object</code>
    * [.settingRealSize(size)](#module_Custom+settingRealSize)
    * [.setRise(rise)](#module_Custom+setRise)
    * [.setTransform(transform)](#module_Custom+setTransform)
    * [.getTransform()](#module_Custom+getTransform) ⇒ <code>Object</code>
    * [.getDataToInject()](#module_Custom+getDataToInject) ⇒ <code>Object</code>
    * [.deselect()](#module_Custom+deselect)
    * [.setStyling(geometry, material)](#module_Custom+setStyling)


* * *

##### injectedRenderer(renderer)
> 렌더러가 주입되다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param |
| --- |
| renderer | 


* * *

##### getEid()
> Event id를 리턴한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  
**Returns**: <code>number</code>
* * *

##### setUuid(uuid)
> uuid를 저장한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param | Type |
| --- | --- |
| uuid | <code>string</code> | 


* * *

##### getUuid()
> uuid를 리턴한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  
**Returns**: <code>null</code>
* * *

##### getType()
> 커스텀 제품의 타입을 리턴한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  
**Returns**: <code>\*</code>
* * *

##### setSize(size)
> 사이즈를 다시 설정한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param | Type |
| --- | --- |
| size | <code>object</code> | 

**Example**  
```javascript
const size = {
    width: 0,
    height: 0,
    depth: 0,
    rise: 0,
}

custom.setSize(size)
```

* * *

##### getSize()
> 현재 사이즈를 리턴한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  
**Returns**: <code>Object</code>
* * *

##### settingRealSize(size)
> size를 다시 설정한다.

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param | Type |
| --- | --- |
| size | <code>array</code> | 

**Example**  
```javascript
const size = [1, 1, 1];

custom.settingRealSize(size);
```

* * *

##### setRise(rise)
> 제품의 높이 값을 설정

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param | Type |
| --- | --- |
| rise | <code>number</code> | 


* * *

##### setTransform(transform)
> Transform 정보를 저장한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param | Type |
| --- | --- |
| transform | <code>object</code> | 

**Example**  
```javascript
const transform = {
    position: [0, 0, 0],
    rotation: [0, 0, 0],
    scale: [0, 0, 0],
}

custom.setTransform(transform);
```

* * *

##### getTransform()
> Transform 정볼르 리턴한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  
**Returns**: <code>Object</code>
* * *

##### getDataToInject()
> 3D에 주입할 데이터를 전달한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  
**Returns**: <code>Object</code>
* * *

##### deselect()
> 선택한 커스텀 상품을 해제한다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

* * *

##### setStyling(geometry, material)
> Custom에 style을 입힌다

**Kind**: instance method of [<code>Custom</code>](#module_Custom)  

| Param | Type |
| --- | --- |
| geometry | <code>object</code> | 
| material | <code>object</code> | 

**Example**  
```javascript
custom.setStyling(geometry, material);
```

* * *


<br>

#### ProductStructure
> 구조설비 상품에 대한 객체


| Param | Type | Description |
| --- | --- | --- |
| params | <code>object</code> | 필수: 구조설비 상품에 대한 정보들을 주입 (예제 참고) |
| token | <code>string</code> |  |
| errorCallback | <code>function</code> |  |

**Example**  
```javascript
// 객체 생성을 하면 API 요청시, request parameters 가 포함되어 전송됩니다.
// UB 내부에서 사용되는 예약어일 뿐이므로 걱정하지 마십시오.

// 응답 Data example :
// Product → https://wsdk.urbanbase.com/crane_js/sample/assets/1

// case1: 문,창 경우일 경우
const window = new Crane.ProductStructure({
          assetId: '', // 필수
          assetUuid: '', // 필수
          type: '', // 필수 'door'|'window'
          width: 0, // Number
          height: 0, // Number
          depth: 0, // Number
          rise: 0, // Number
      });

// case2: 구조설비 (굽도리, 몰딩, 니치, 개구부) 의 경우
const productStructure = new Crane.ProductStructure({
          type: '', // 필수 'pillar'|'crossbeam'|'opening'|'niche'|'moulding'|'baseboard'
          width: 0, // Number
          height: 0, // Number
          depth: 0, // Number
          rise: 0, // Number
      });
```

* [ProductStructure](#module_ProductStructure)
    * [.isProductType()](#module_ProductStructure+isProductType) ⇒ <code>boolean</code>
    * [.isMouldingBaseboardType()](#module_ProductStructure+isMouldingBaseboardType) ⇒ <code>boolean</code>
    * [.injectedRenderer(renderer)](#module_ProductStructure+injectedRenderer)
    * [.getEid()](#module_ProductStructure+getEid) ⇒ <code>number</code>
    * [.setUuid(uuid)](#module_ProductStructure+setUuid)
    * [.getUuid()](#module_ProductStructure+getUuid) ⇒ <code>string</code>
    * [.getType()](#module_ProductStructure+getType) ⇒ <code>string</code>
    * [.setSize(size)](#module_ProductStructure+setSize)
    * [.getSize()](#module_ProductStructure+getSize) ⇒ <code>Object</code>
    * [.setTransform(transform)](#module_ProductStructure+setTransform)
    * [.getTransform()](#module_ProductStructure+getTransform) ⇒ <code>Object</code>
    * [.getDataToInject()](#module_ProductStructure+getDataToInject) ⇒ <code>Object</code>
    * [.unselect()](#module_ProductStructure+unselect)
    * [.remove()](#module_ProductStructure+remove)
    * [.setStyling(geometry, material)](#module_ProductStructure+setStyling)
    * [.getAssetId()](#module_ProductStructure+getAssetId) ⇒ <code>\*</code>
    * [.getAssetUuid()](#module_ProductStructure+getAssetUuid) ⇒ <code>null</code> \| <code>string</code>
    * [.getTitle()](#module_ProductStructure+getTitle) ⇒ <code>string</code> \| <code>string</code>
    * [.getRise()](#module_ProductStructure+getRise) ⇒ <code>number</code>
    * [.getStyleId()](#module_ProductStructure+getStyleId) ⇒ <code>\*</code>
    * [.getStyle()](#module_ProductStructure+getStyle) ⇒ <code>\*</code>
    * [.getOpenType()](#module_ProductStructure+getOpenType) ⇒ <code>boolean</code>
    * [.getUrl()](#module_ProductStructure+getUrl) ⇒ <code>\*</code>
    * [.settingRealSize(size)](#module_ProductStructure+settingRealSize)
    * [.flipHorizontal()](#module_ProductStructure+flipHorizontal)
    * [.setDefaultStyle()](#module_ProductStructure+setDefaultStyle)
    * [.setStyleId(styleId)](#module_ProductStructure+setStyleId)
    * [.setOriginalSize(size)](#module_ProductStructure+setOriginalSize)
    * [.getOriginalSize()](#module_ProductStructure+getOriginalSize) ⇒ <code>Object</code>
    * [.setGeometryStyles()](#module_ProductStructure+setGeometryStyles)
    * [.getGeometryData()](#module_ProductStructure+getGeometryData) ⇒ <code>\*</code>
    * [.setGeometryMaterialId(material_id)](#module_ProductStructure+setGeometryMaterialId)
    * [.getGeometryMaterialIds()](#module_ProductStructure+getGeometryMaterialIds) ⇒ <code>Array</code>
    * [.getOriginGeometryMaterialIds()](#module_ProductStructure+getOriginGeometryMaterialIds) ⇒ <code>Array</code>
    * [.getDefaultGeometryStyle()](#module_ProductStructure+getDefaultGeometryStyle) ⇒ <code>object</code>
    * [.changeDefaultStyle()](#module_ProductStructure+changeDefaultStyle)
    * [.resetGeometryMaterialIds()](#module_ProductStructure+resetGeometryMaterialIds)


* * *

##### isProductType()
> 문,창과 같은 제품 타입의 structure인지 체크

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>boolean</code>
* * *

##### isMouldingBaseboardType()
> 문,창과 같은 제품 타입의 structure인지 체크

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>boolean</code>
* * *

##### injectedRenderer(renderer)
> 렌더러가 주입되다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param |
| --- |
| renderer | 


* * *

##### getEid()
> Event id를 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>number</code>
* * *

##### setUuid(uuid)
> uuid를 저장한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Type |
| --- | --- |
| uuid | <code>string</code> | 


* * *

##### getUuid()
> uuid를 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>string</code>
* * *

##### getType()
> 커스텀 제품의 타입을 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>string</code>
* * *

##### setSize(size)
> 사이즈를 다시 설정한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Type | Description |
| --- | --- | --- |
| size | <code>object</code> | * @example const size = {     width: 0,     height: 0,     depth: 0,     rise: 0, } productStructure.setSize(size) |


* * *

##### getSize()
> 현재 사이즈를 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>Object</code>
* * *

##### setTransform(transform)
> Transform 정보를 저장한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param |
| --- |
| transform | 

**Example**  
```javascript
const transform = {
    position: [0, 0, 0],
    rotation: [0, 0, 0],
    scale: [0, 0, 0],
}

productStructure.setTransform(transform);
```

* * *

##### getTransform()
> Transform 정볼르 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>Object</code>
* * *

##### getDataToInject()
> 3D에 주입할 데이터를 전달한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>Object</code>
* * *

##### unselect()
> 선택한 커스텀 상품을 해제한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *

##### remove()
> 상품을 삭제한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *

##### setStyling(geometry, material)
> Custom에 style을 입힌다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Type |
| --- | --- |
| geometry | <code>object</code> | 
| material | <code>object</code> | 


* * *

##### getAssetId()
> assetId 를 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>\*</code>
* * *

##### getAssetUuid()
> assetUuid 를 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>null</code> \| <code>string</code>
* * *

##### getTitle()
> 제품명을 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>string</code> \| <code>string</code>
* * *

##### getRise()
> rise 값을 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>number</code>
* * *

##### getStyleId()
> style id를 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>\*</code>
* * *

##### getStyle()
> 스타일 정보를 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>\*</code>
* * *

##### getOpenType()
> 개페방향을 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>boolean</code>
* * *

##### getUrl()
> url을 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>\*</code>
* * *

##### settingRealSize(size)
> size를 다시 설정한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Description |
| --- | --- |
| size | [] |

**Example**  
```javascript
const size = [1, 1, 1];

productStructure.settingRealSize(size);
```

* * *

##### flipHorizontal()
> 구조설비 수평 반전

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *

##### setDefaultStyle()
> 기본 스타일 값을 설정한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *

##### setStyleId(styleId)
> style id를 저장한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Type |
| --- | --- |
| styleId | <code>string</code> | 


* * *

##### setOriginalSize(size)
> 기본 사이즈를 설정한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Type |
| --- | --- |
| size | <code>array</code> | 

**Example**  
```javascript
const size = [1,1,1]
productStructure.setOriginalSize(size);
```

* * *

##### getOriginalSize()
> 기본 사이즈를 반환한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>Object</code>
* * *

##### setGeometryStyles()
> 지오메트리 매터리얼에 대한 정리를 한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *

##### getGeometryData()
> 지오메터리 데이터를 리턴한다.

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>\*</code>
* * *

##### setGeometryMaterialId(material_id)
> 지오메트리 매터리얼 id를 설정한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

| Param | Type |
| --- | --- |
| material_id | <code>string</code> | 


* * *

##### getGeometryMaterialIds()
> 현재 지오메트리 id 리스트를 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>Array</code>
* * *

##### getOriginGeometryMaterialIds()
> 기존 지오메트리 id 리스트를 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>Array</code>
* * *

##### getDefaultGeometryStyle()
> DefaultGeometryStyle을 리턴한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  
**Returns**: <code>object</code>
* * *

##### changeDefaultStyle()
> 기존 스타일로 변경한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *

##### resetGeometryMaterialIds()
> 지오메트리 매터리얼 리스트를 초기화한다

**Kind**: instance method of [<code>ProductStructure</code>](#module_ProductStructure)  

* * *


<br>

#### Post
> 홈 디자이닝 데이터를 로드하는 객체 ( 도면, 제품들의 데이터를 로드 )


| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | 필수: postId |
| defaultMaterialId | <code>string</code>, <code>null</code> |  |
| token | <code>string</code> |  |
| errorCallback | <code>function</code> |  |

**Example**  
```javascript
// 객체 생성을 하면 GET API 요청시, request parameters 가 포함되어 전송됩니다.
// UB 내부에서 사용되는 예약어일 뿐이므로 걱정하지 마십시오.

// 응답 Data example :
// Post → https://wsdk.urbanbase.com/crane_js/sample/posts/1

const post = new Crane.Post( id, null, token );
```

* [Post](#module_Post)
    * [.injectedRenderer(renderer)](#module_Post+injectedRenderer)
    * [.setStructure(structure)](#module_Post+setStructure)
    * [.setProduct(product)](#module_Post+setProduct)
    * [.setCustom(custom)](#module_Post+setCustom)
    * [.setProductStructure(product)](#module_Post+setProductStructure)
    * [.setCapture(capture)](#module_Post+setCapture)
    * [.setSetting(setting)](#module_Post+setSetting)
    * [.getStructure()](#module_Post+getStructure) ⇒ <code>\*</code>
    * [.getProducts()](#module_Post+getProducts) ⇒ <code>\*</code>
    * [.getCustoms()](#module_Post+getCustoms) ⇒ <code>\*</code>
    * [.getCaptures()](#module_Post+getCaptures) ⇒ <code>\*</code>
    * [.getSettings()](#module_Post+getSettings) ⇒ <code>\*</code>
    * [.getProductStructures()](#module_Post+getProductStructures) ⇒ <code>\*</code>
    * [.getPostBuildingHoes()](#module_Post+getPostBuildingHoes) ⇒ <code>\*</code>
    * [.getPostType()](#module_Post+getPostType) ⇒ <code>string</code>


* * *

##### injectedRenderer(renderer)
> 렌더러가 주입되다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| renderer | 


* * *

##### setStructure(structure)
> 도면을 설정한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| structure | 


* * *

##### setProduct(product)
> 제품을 설정한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| product | 


* * *

##### setCustom(custom)
> 커스텀 제품을 설정한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| custom | 


* * *

##### setProductStructure(product)
> 구조설비를 설정한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| product | 


* * *

##### setCapture(capture)
> 캡쳐 정보를 설정한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| capture | 


* * *

##### setSetting(setting)
> 그림자, 투명도 등의 정보를 셋팅한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  

| Param |
| --- |
| setting | 


* * *

##### getStructure()
> 도면 객체를 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getProducts()
> 제품들을 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getCustoms()
> 커스템 제품들을 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getCaptures()
> 캡쳐들을 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getSettings()
> 셋팅 정보를 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getProductStructures()
> 구조설비 객체들을 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getPostBuildingHoes()
> 동호수 정보를 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>\*</code>
* * *

##### getPostType()
> 플랜의 타입을 리턴한다

**Kind**: instance method of [<code>Post</code>](#module_Post)  
**Returns**: <code>string</code>
* * *


<br>

#### PostModel
> 홈디자이닝 데이터에 대한 API


* [PostModel](#module_PostModel)
    * [.getData(id)](#module_PostModel+getData) ⇒ <code>Promise.&lt;\*&gt;</code>
    * [.getMaterials(ids)](#module_PostModel+getMaterials) ⇒ <code>Promise.&lt;\*&gt;</code>


* * *

##### getData(id)
> 홈디자이님 데이터를 가져온다

**Kind**: instance method of [<code>PostModel</code>](#module_PostModel)  
**Returns**: <code>Promise.&lt;\*&gt;</code>
| Param |
| --- |
| id | 


* * *

##### getMaterials(ids)
> 메터리얼 데이터를 가져온다

**Kind**: instance method of [<code>PostModel</code>](#module_PostModel)  
**Returns**: <code>Promise.&lt;\*&gt;</code>
| Param |
| --- |
| ids | 


* * *


<br>

#### Camera
> 카메라의 설정에 대한 객체


* [Camera](#module_Camera)
    * [.setViewMode(mode)](#module_Camera+setViewMode)
    * [.setViewAngle(presetView)](#module_Camera+setViewAngle)
    * [.setPersonHeight(personHeight)](#module_Camera+setPersonHeight)
    * [.setFieldOfView(fov)](#module_Camera+setFieldOfView)
    * [.activateRotation()](#module_Camera+activateRotation)
    * [.deactivateRotation()](#module_Camera+deactivateRotation)
    * [.activatePanning()](#module_Camera+activatePanning)
    * [.deactivatePanning()](#module_Camera+deactivatePanning)
    * [.screenShot(hasBackground)](#module_Camera+screenShot)
    * [.isOrbit()](#module_Camera+isOrbit) ⇒ <code>boolean</code>
    * [.isFirstPerson()](#module_Camera+isFirstPerson) ⇒ <code>boolean</code>
    * [.isOrthographic()](#module_Camera+isOrthographic) ⇒ <code>boolean</code>


* * *

##### setViewMode(mode)
> 카메라의 모드를 설정한다 (Orbit or First Person)

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

| Param | Default |
| --- | --- |
| mode | <code>observer</code> | 


* * *

##### setViewAngle(presetView)
> 카메라의 위치를 설정한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

| Param |
| --- |
| presetView | 


* * *

##### setPersonHeight(personHeight)
> First Person 모드 일 때, 사람의 키를 설정한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

| Param |
| --- |
| personHeight | 


* * *

##### setFieldOfView(fov)
> 카메라의 시야각을 설정한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

| Param | Default |
| --- | --- |
| fov | <code>60</code> | 


* * *

##### activateRotation()
> 카메라의 회전을 활성화 한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

* * *

##### deactivateRotation()
> 카메라의 회전을 비활성화 한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

* * *

##### activatePanning()
> 카메라의 panning을 활성화 한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

* * *

##### deactivatePanning()
> 카메라의 panning을 비활성화 한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

* * *

##### screenShot(hasBackground)
> 스크린 샷을 찍는다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  

| Param | Default |
| --- | --- |
| hasBackground | <code>true</code> | 


* * *

##### isOrbit()
> observer 모드인지 확인한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  
**Returns**: <code>boolean</code>
* * *

##### isFirstPerson()
> 1인칭 모드인지 확인한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  
**Returns**: <code>boolean</code>
* * *

##### isOrthographic()
> 직교투영 모드인지 확인한다

**Kind**: instance method of [<code>Camera</code>](#module_Camera)  
**Returns**: <code>boolean</code>
* * *


<br>

#### Light
> 빛 설정에 대한 객체


* [Light](#module_Light)
    * [.getCoreEid()](#module_Light+getCoreEid) ⇒ <code>string</code>
    * [.getEid()](#module_Light+getEid) ⇒ <code>string</code>
    * [.setTime(dateAndTime)](#module_Light+setTime)


* * *

##### getCoreEid()
> core id 를 리턴한다

**Kind**: instance method of [<code>Light</code>](#module_Light)  
**Returns**: <code>string</code>
* * *

##### getEid()
> id를 리턴한다

**Kind**: instance method of [<code>Light</code>](#module_Light)  
**Returns**: <code>string</code>
* * *

##### setTime(dateAndTime)
> 시간을 설정한다

**Kind**: instance method of [<code>Light</code>](#module_Light)  

| Param |
| --- |
| dateAndTime | 


* * *


<br>

#### Paint
> 벽지/바닥재의 스타일을 변경하는 객체


* [Paint](#module_Paint)
    * [.startStyling(material, angle)](#module_Paint+startStyling)
    * [.stopStyling()](#module_Paint+stopStyling)


* * *

##### startStyling(material, angle)
> 벽지/바닥재의 스타일 변경을 시작한다

**Kind**: instance method of [<code>Paint</code>](#module_Paint)  

| Param |
| --- |
| material | 
| angle | 


* * *

##### stopStyling()
> 벽지/바닥재의 스타일 변경을 끝낸다

**Kind**: instance method of [<code>Paint</code>](#module_Paint)  

* * *


<br>

#### Ruler
> 길이/면적을 재는 객체


* [Ruler](#module_Ruler)
    * [.startMeasureDistance()](#module_Ruler+startMeasureDistance)
    * [.stopMeasureDistance()](#module_Ruler+stopMeasureDistance)
    * [.startMeasureArea()](#module_Ruler+startMeasureArea)
    * [.stopMeasureArea()](#module_Ruler+stopMeasureArea)


* * *

##### startMeasureDistance()
> 길이 측정을 시작한다

**Kind**: instance method of [<code>Ruler</code>](#module_Ruler)  

* * *

##### stopMeasureDistance()
> 길이 측정을 중단한다

**Kind**: instance method of [<code>Ruler</code>](#module_Ruler)  

* * *

##### startMeasureArea()
> 면적 측정을 시작한다

**Kind**: instance method of [<code>Ruler</code>](#module_Ruler)  

* * *

##### stopMeasureArea()
> 면적 측정을 중단한다

**Kind**: instance method of [<code>Ruler</code>](#module_Ruler)  

* * *


<br>

#### Setting
> 플레이어의 기본 설정에 대한 객체


* [Setting](#module_Setting)
    * [.setSDKMode(mode)](#module_Setting+setSDKMode)
    * [.getSDKMode()](#module_Setting+getSDKMode) ⇒ <code>string</code> \| <code>string</code>
    * [.setScreenResolution(width, height)](#module_Setting+setScreenResolution)
    * [.setScreenQuality(quality)](#module_Setting+setScreenQuality)
    * [.setGraphicQuality(quality)](#module_Setting+setGraphicQuality)
    * [.setShadowType(shadowType)](#module_Setting+setShadowType)
    * [.setVSync(vsync)](#module_Setting+setVSync)
    * [.setSkyboxGradient(bgColor)](#module_Setting+setSkyboxGradient)
    * [.setProductCollision(active)](#module_Setting+setProductCollision)
    * [.setProductFreeMovement(active)](#module_Setting+setProductFreeMovement)
    * [.setGrid(active)](#module_Setting+setGrid)
    * [.setMotionBlur(active)](#module_Setting+setMotionBlur)
    * [.setBloom(active, intensity, threshold)](#module_Setting+setBloom)
    * [.setVignette(active, intensity)](#module_Setting+setVignette)
    * [.setMouseSensitivity(value)](#module_Setting+setMouseSensitivity)
    * [.setReverseMouseHorizontal(active)](#module_Setting+setReverseMouseHorizontal)
    * [.setReverseMouseVertical(active)](#module_Setting+setReverseMouseVertical)
    * [.setReverseMouseWheel(active)](#module_Setting+setReverseMouseWheel)


* * *

##### setSDKMode(mode)
> SDK 모드를 설정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param |
| --- |
| mode | 


* * *

##### getSDKMode()
> 설정된 SDK 모드를 리턴한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  
**Returns**: <code>string</code> \| <code>string</code>
* * *

##### setScreenResolution(width, height)
> 화면의 해상도를 설정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| width | <code>400</code> | 
| height | <code>400</code> | 


* * *

##### setScreenQuality(quality)
> 화면 품질을 설정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| quality | <code>0</code> | 


* * *

##### setGraphicQuality(quality)
> 화면 품질을 설정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| quality | <code>0</code> | 


* * *

##### setShadowType(shadowType)
> 그림자의 타입을 설정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default | Description |
| --- | --- | --- |
| shadowType | <code>none</code> | 'none'|'hard'|'soft' |


* * *

##### setVSync(vsync)
> Vsync를 설정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| vsync | <code>0</code> | 


* * *

##### setSkyboxGradient(bgColor)
> 플레이어의 백그라운드 컬러를 지정한다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param |
| --- |
| bgColor | 


* * *

##### setProductCollision(active)
> 상품의 충돌을 활성/비활성 시킨다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>1</code> | 


* * *

##### setProductFreeMovement(active)
> 상품의 자유이동을 활성/비활성화 시킨다.

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>1</code> | 


* * *

##### setGrid(active)
> 그리드를 활성/비활성 시킨다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>0</code> | 


* * *

##### setMotionBlur(active)
> 모션에 대한 블러를 활성/비활성 시킨다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>true</code> | 


* * *

##### setBloom(active, intensity, threshold)
> 빛이 세는 효과를 활성/비활성 시킨다

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>true</code> | 
| intensity | <code>1</code> | 
| threshold | <code>0.9</code> | 


* * *

##### setVignette(active, intensity)
> 스크린 주변 밝기 조절

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>true</code> | 
| intensity | <code>0.3</code> | 


* * *

##### setMouseSensitivity(value)
> 마우스 민감도 조절

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| value | <code>50</code> | 


* * *

##### setReverseMouseHorizontal(active)
> 마우스 수평 반전

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>0</code> | 


* * *

##### setReverseMouseVertical(active)
> 마우스 수직 반전

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>0</code> | 


* * *

##### setReverseMouseWheel(active)
> 마우스 휠 반전

**Kind**: instance method of [<code>Setting</code>](#module_Setting)  

| Param | Default |
| --- | --- |
| active | <code>0</code> | 


* * *


<br>

#### History
> 히스토리를 관리하는 객체


* [History](#module_History)
    * [.getCoreEid()](#module_History+getCoreEid) ⇒ <code>string</code>
    * [.getEid()](#module_History+getEid) ⇒ <code>string</code>
    * [.undo()](#module_History+undo)
    * [.redo()](#module_History+redo)
    * [.abledToUndo()](#module_History+abledToUndo)
    * [.abledToRedo()](#module_History+abledToRedo)
    * [.clear()](#module_History+clear)


* * *

##### getCoreEid()
> core id 를 리턴한다

**Kind**: instance method of [<code>History</code>](#module_History)  
**Returns**: <code>string</code>
* * *

##### getEid()
> id를 리턴한다

**Kind**: instance method of [<code>History</code>](#module_History)  
**Returns**: <code>string</code>
* * *

##### undo()
> 이전 상태로 되돌린다

**Kind**: instance method of [<code>History</code>](#module_History)  

* * *

##### redo()
> 이후 상태로 되돌린다

**Kind**: instance method of [<code>History</code>](#module_History)  

* * *

##### abledToUndo()
> 이전 상태로 되돌리기가 가능한지 확인한다

**Kind**: instance method of [<code>History</code>](#module_History)  

* * *

##### abledToRedo()
> 이후 상태로 되돌리기가 가능한지 확인한다

**Kind**: instance method of [<code>History</code>](#module_History)  

* * *

##### clear()
> 모든 히스토리를 초기화한다

**Kind**: instance method of [<code>History</code>](#module_History)  

* * *


<br>

#### Renderer ⇐ <code>EventEmitter</code>
> unity 화면을 렌더링하는 객체

**Extends**: <code>EventEmitter</code>  

* [Renderer](#module_Renderer) ⇐ <code>EventEmitter</code>
    * [.getEid()](#module_Renderer+getEid) ⇒ <code>number</code>
    * [.getId()](#module_Renderer+getId) ⇒ <code>string</code>


* * *

##### getEid()
> Event id를 리턴한다

**Kind**: instance method of [<code>Renderer</code>](#module_Renderer)  
**Returns**: <code>number</code>
* * *

##### getId()
> Element ID를 리턴한다

**Kind**: instance method of [<code>Renderer</code>](#module_Renderer)  
**Returns**: <code>string</code>
* * *

