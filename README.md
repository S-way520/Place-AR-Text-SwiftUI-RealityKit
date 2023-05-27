# Place-AR-Text-SwiftUI-RealityKit-
Place blue AR text
# The first part
![IMG_1222](https://github.com/S-way520/Place-AR-Text-SwiftUI-RealityKit-/assets/95877651/782dfc99-342b-4f31-9a2a-4505b8be6ec2)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            Reality()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import RealityKit
struct Reality: View {
    var body: some View {
        ARViewContainer().edgesIgnoringSafeArea(.all)
    }
}
struct ARViewContainer: UIViewRepresentable {
    func makeUIView(context: Context) -> ARView {
        let arView = ARView(frame: .zero, cameraMode: .ar, automaticallyConfigureSession: true)
        let anchorEntity = AnchorEntity(plane: .horizontal)
        let MeshText = MeshResource.generateText("AR Text", extrusionDepth: 0.02, font: .systemFont(ofSize: 0.2/2), containerFrame: .zero, alignment: .center, lineBreakMode: .byCharWrapping)//文字(Text)
        let material = SimpleMaterial(color: .blue, isMetallic: true)
        let ARentity = ModelEntity(mesh: MeshText, materials: [material])
        anchorEntity.addChild(ARentity)
        arView.scene.anchors.append(anchorEntity)
        return arView
    }
    func updateUIView(_ uiView: ARView, context: Context) {
    }
}
```
