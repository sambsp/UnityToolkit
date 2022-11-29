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
int LayerMask.LayerNameToLayer(string name);

// get a layer name
string LayerMask.LayerToName(int layer)
