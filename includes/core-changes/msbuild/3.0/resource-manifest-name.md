---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968294"
---
### <a name="resource-manifest-file-names"></a>Kaynak bildirimi dosya adları

.NET Core 3.0'dan başlayarak oluşturulan kaynak bildirimi dosya adı değişti.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="change-description"></a>Açıklamayı değiştir

MSBuild proje dosyasındaki bir kaynak (*.resx*) dosyası için [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) meta verileri ayarlandığında ,.NET Core 3.0'dan önce oluşturulan bildirim adı *Namespace.Classname.resources*idi. [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) ayarlanmadığında, oluşturulan bildirim adı *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*oldu.

.NET Core 3.0'dan başlayarak, bir *.resx* dosyası aynı adı taşıyan bir kaynak dosyayla birlikte konumlandığında, örneğin Windows Forms uygulamalarında kaynak bildirimi adı kaynak dosyadaki ilk türün tam adından oluşturulur. Örneğin, *Type.cs* *Type.resx*ile birlikte bulunursa, oluşturulan bildirim adı *Namespace.Classname.resources'tır.* Ancak, *.resx* dosyasının `EmbeddedResource` özelliğindeki özniteliklerden herhangi birini değiştirirseniz, oluşturulan bildirim dosyası adı farklı olabilir:

- `LogicalName` Özellik teki öznitelik `EmbeddedResource` ayarlanırsa, bu değer kaynak bildirimi dosya adı olarak kullanılır.

  Örnekler:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Oluşturulan kaynak bildirimi dosya adı**: *SomeName.resources* *(.resx* dosya adı veya kültürü veya diğer meta verilerden bağımsız olarak).

- `LogicalName` Ayarlanmaz, ancak `ManifestResourceName` `EmbeddedResource` özellik üzerindeki öznitelik ayarlanırsa, değeri, dosya uzantısı *.resources*ile birlikte, kaynak bildirimi dosya adı olarak kullanılır.

  Örnekler:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Oluşturulan kaynak bildirimi dosya adı**: *SomeName.resources* veya *SomeName.fr-FR.resources*.

- Önceki kurallar geçerli değilse ve `DependentUpon` `EmbeddedResource` öğedeki öznitelik bir kaynak dosyasına ayarlanırsa, kaynak dosyasındaki birinci sınıfın tür adı kaynak bildirimi dosya adında kullanılır. Daha spesifik olarak, oluşturulan dosya adı *\[Namespace.Classname olduğunu. Kültür].kaynaklar*.

  Örnekler:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Oluşturulan kaynak bildirimi dosya adı**: *Namespace.Classname.resources* veya `Namespace.Classname` *Namespace.Classname.fr-FR.resources* *(MyTypes.cs'daki*birinci sınıfın adı nerededir).

- Önceki kurallar `EmbeddedResourceUseDependentUponConvention` geçerli değilse, (.NET `true` Core için varsayılan varsayılan) ve aynı temel dosya adı olan bir *.resx* dosyasıyla birlikte bir kaynak dosyası varsa, *.resx* dosyası eşleşen kaynak dosyaya bağımlı hale getirilir ve oluşturulan ad önceki kuraldakiyle aynıdır. Bu, .NET Core projeleri için "varsayılan ayarlar" kuralıdır.
  
  Örnekler:
  
  MyTypes.cs *MyTypes.cs* ve *MyTypes.resx* veya *MyTypes.fr-FR.resx* dosyaları aynı klasörde bulunur.
  
  **Oluşturulan kaynak bildirimi dosya adı**: *Namespace.Classname.resources* veya `Namespace.Classname` *Namespace.Classname.fr-FR.resources* *(MyTypes.cs'daki*birinci sınıfın adı nerededir).

- Önceki kuralların hiçbiri geçerli değilse, oluşturulan kaynak bildirimi dosya adı *RootNamespace.RelativePathWithDotsForSlashes olduğunu.\[ Kültür.] kaynaklar*. Göreli yol, ayarlanırsa `Link` `EmbeddedResource` öğenin özniteliğinin değeridir. Aksi takdirde, göreli yol `Identity` `EmbeddedResource` öğenin özniteliğinin değeridir. Visual Studio'da bu, çözüm gezgininde proje kökünden dosyaya giden yoldur.

#### <a name="recommended-action"></a>Önerilen eylem

Oluşturulan bildirim adlarıyla memnun değilseniz şunları yapabilirsiniz:

- Kaynak dosyası meta verilerinizi daha önce açıklanan adlandırma kurallarından birine göre değiştirin.

- Yeni kuralı tamamen devre dışı bırakmak için proje dosyanızda ayarlayın: `EmbeddedResourceUseDependentUponConvention` `false`

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > `LogicalName` Öznitelikler varsa, bunların değerleri yine de oluşturulan dosya adı için `ManifestResourceName` kullanılır.

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok
