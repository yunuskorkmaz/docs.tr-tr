---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451907"
---
### <a name="resource-manifest-file-names"></a>Kaynak bildirim dosyası adları

.NET Core 3,0 ' den başlayarak, oluşturulan kaynak bildirim dosyası adı değişmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ' den önce, MSBuild proje dosyasındaki bir kaynak ( *. resx*) dosyası için [bir veri kümesi ayarlandığında,](/visualstudio/msbuild/common-msbuild-project-items#compile) oluşturulan bildirim adı *Namespace. ClassName. resources*idi. [Dependentno](/visualstudio/msbuild/common-msbuild-project-items#compile) ayarlanınca, oluşturulan bildirim adı *Namespace. ClassName. FolderPathRelativeToRoot. Culture. resources*idi.

.NET Core 3,0 ' den itibaren, bir *. resx* dosyası aynı ada sahip bir kaynak dosyayla birlikte kullanılırken, örneğin Windows Forms uygulamalarda kaynak bildirimi adı kaynak dosyadaki ilk türün tam adından oluşturulur. Örneğin, *Type.cs* *Type. resx*ile birlikte bulunuyorsa, oluşturulan bildirim adı *Namespace. ClassName. resources*olur. Ancak, *. resx* dosyası için `EmbeddedResource` özelliğindeki özniteliklerin herhangi birini değiştirirseniz, oluşturulan bildirim dosyası adı farklı olabilir:

- `EmbeddedResource` özelliğindeki `LogicalName` özniteliği ayarlandıysa, bu değer kaynak bildirimi dosya adı olarak kullanılır.

  Örnekler:

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Oluşturulan kaynak bildirim dosyası adı**: *someName. resources* ( *. resx* dosya adı veya kültür ya da diğer meta veriler ne olursa olsun).

- `LogicalName` ayarlanmamışsa, ancak `EmbeddedResource` özelliğindeki `ManifestResourceName` özniteliği ayarlanmışsa, kaynak bildirim dosyası adı olarak, değeri *. resources*ile birleştirilir.

  Örnekler:

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Kaynak bildirim dosyası adı oluşturuldu**: *someName. resources* veya *someName.fr-fr. resources*.

- Önceki kurallar uygulanmıyorsanız ve `EmbeddedResource` öğesindeki `DependentUpon` özniteliği bir kaynak dosyaya ayarlanırsa, kaynak dosyadaki ilk sınıfın tür adı kaynak bildirim dosyası adında kullanılır. Daha belirgin olarak, oluşturulan dosya adı *Namespace. Classname\[. Kültür]. resources*.

  Örnekler:

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Oluşturulan kaynak bildirim dosyası adı**: *Namespace. ClassName. resources* veya *Namespace.ClassName.fr-fr. resources* (`Namespace.Classname`, *MyTypes.cs*içindeki ilk sınıfın adıdır).

- Önceki kurallar uygulanmamışsa, `EmbeddedResourceUseDependentUponConvention` `true` (.NET Core için varsayılan) ve aynı temel dosya adına sahip bir *. resx* dosyası ile birlikte bulunan bir kaynak dosya varsa, *. resx* dosyası eşleşen kaynak dosyaya bağımlıdır ve oluşturulan ad önceki kuraldaki ile aynı olur. Bu, .NET Core projeleri için "varsayılan ayarlar" kuralıdır.
  
  Örnekler:
  
  *MyTypes.cs* ve *myTypes. resx* veya *MyTypes.fr-fr. resx* dosyaları aynı klasörde bulunur.
  
  **Oluşturulan kaynak bildirim dosyası adı**: *Namespace. ClassName. resources* veya *Namespace.ClassName.fr-fr. resources* (`Namespace.Classname`, *MyTypes.cs*içindeki ilk sınıfın adıdır).
    
- Önceki kuralların hiçbiri uygulanmadığı takdirde, oluşturulan kaynak bildirim dosyası adı *RootNamespace. Relativepathwithdotsforçizgiler.\[kültür.] kaynaklar*. Göreli yol, ayarlandıysa `EmbeddedResource` öğenin `Link` özniteliğinin değeridir. Aksi takdirde, göreli yol `EmbeddedResource` öğesinin `Identity` özniteliğinin değeridir. Visual Studio 'da, bu yol proje kökünden Çözüm Gezgini dosyanın yoludur.

#### <a name="recommended-action"></a>Önerilen eylem

Oluşturulan bildirim adlarından memnun kaldıysanız şunları yapabilirsiniz:

- Kaynak dosyası meta verilerinizi, daha önce açıklanan adlandırma kurallarından birine göre değiştirin.

- Yeni kuralı tamamen devre dışı bırakmak için `EmbeddedResourceUseDependentUponConvention`, proje dosyanızda `false` olarak ayarlayın:

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > `LogicalName` veya `ManifestResourceName` öznitelikleri varsa, bu değerler oluşturulan dosya adı için yine de kullanılacaktır.

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

YOK
