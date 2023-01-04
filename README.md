# UnityToolkit
Collection of tech of Unity3d

# 1, Locate camera to position, after that, camera will lookat the target automatically

```c#
// get the camera transform
Transform cameraTransform = Global.Instance.FindMainCameraTransform();
Debug.Assert(cameraTransform != null);

// let's get a position for initialize
Vector3 position = targetGameObject.transform.position;
// then get the camera forward direction in world space (camera forward in local space is always Vector3.forward)
Vector3 direction = cameraTransform.TransformDirection(Vector3.forward);
direction.Normalize();
// now we get the right position for camera transform
position -= direction * 5f;
// set camera transform's position
cameraTransform.position = position;

# 2, GameObject Layer Mask
// get a mask can be used in Physics.Raycast
int LayerMask.GetMask(string[] layerNameArray);

// get a layer integer from given name, need to use 1 << layer for Physics.Raycast using
int LayerMask.NameToLayer(string name);

// get a layer name
string LayerMask.LayerToName(int layer)

# 3, UI adaption

You should have a design resolution first.
Then you make a UI canvas, on the "Canvas Scaler" component, "UI Scale Mode" choose "Scale With Screen Size". Then fill Reference Resolution with your design resolution.

Tip:
if there is ScrollView with dynamic content, you should add your content, for example, one row, by using transform.SetParent(t, false);

# 4, WebGL javascript

You can customize your template by add a template to Assets/WebGL Templates folder, copy one folder from Unity Engine (for example, on mac, it's path is "Unity/PlaybackEngines/WebGLSupport/WebGL Templates"). And add <script src="">[file.js]</script> below unity's script tag. 

In file.js, put your code there. For unityInstance, you can keep reference at callback of createUnityInstance, use window.unityInstance = unityInstance;
Then at your file.js, you can use unityInstance as window.unityInstance anywhere.

To call C# code, you use window.unityInstance.SendMessage()

# 5, Unity Remote Debug

To test 'touch' feature, Unity remote is a tool (application) to make thing easy. For iOS, download "Unity Remote 5" from appstore. Then
a, in unity editor, switch active settings to iOS
b, link iPhone/iPad with a wire to your PC. For sure, you can install iTunes to see whether you can see your device on the iTunes.
c, unity editor, edit/project settings/editor, unity remote/device, should see Any iOS device and your iOS device name. Choose your iOS device.
d, play, you can now see the screen sync to your device.


