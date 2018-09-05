---
title: Paketleme ve özel My uzantılarını (Visual Basic) dağıtma
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565248"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Paketleme ve özel My uzantılarını (Visual Basic) dağıtma

Visual Basic özel dağıtmanız için kolay bir yol sağlar `My` Visual Studio şablonları kullanarak ad alanı uzantıları. Kendisi için bir proje şablonu oluşturuyorsanız, sizin `My` uzantıları bütünleyici yeni proje türünü, yalnızca kendi özel içerebilir `My` proje şablonu dışarı aktardığınızda uzantı kodu. Proje şablonları dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).

Varsa özel `My` uzantısıdır tek bir kod dosyasında, dosyanın her türden Visual Basic proje kullanıcıları ekleyebileceğiniz öğe şablonu dışarı aktarabilirsiniz. Ardından ek özellikleri ve özel davranışı etkinleştirmek için öğe şablonu özelleştirebilir `My` Visual Basic projesinde uzantısı. Bu özellikler şunları içerir:

- Kendi özel yönetmenize izin vererek `My` uzantısından **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa.

- Özel otomatik olarak ekleme `My` uzantısı için belirtilen derlemeyi bir başvuru olduğunda, bir projeye eklenir.

- Gizleme `My` uzantı öğesi şablonunda **Öğe Ekle** iletişim kutusunu listeden proje öğelerinin bulunmaz.

Bu konuda bir özel paket anlatılmaktadır `My` uzantısı alanından yönetilebilir bir gizli öğe şablonu olarak **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa. Özel `My` uzantısı eklenebilir otomatik olarak belirtilen bir derlemeye başvuru için bir proje eklendiğinde.

## <a name="create-a-my-namespace-extension"></a>Oluşturma bir ad alanı uzantısı

Bir dağıtım paketi için özel bir oluşturmanın ilk adımı `My` bir uzantısı olarak tek bir kod dosyası oluşturmak için uzantısıdır. Ayrıntıları ve özel bir oluşturma hakkında yönergeler `My` uzantısı bkz [Visual Basic'te My Namespace genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Dışarı aktarma bir öğe şablonu olarak ad alanı uzantısı

İçeren bir kod dosyası oluşturduktan sonra `My` ad alanı uzantısı için kod dosyasını Visual Studio öğesi şablon olarak dışarı aktarabilirsiniz. Bir dosya Visual Studio öğesi şablon olarak dışarı aktarma yönergeleri için bkz [nasıl yapılır: öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Varsa, `My` ad alanı uzantısı belirli bir derleme üzerinde bir bağımlılık içeriyor, otomatik olarak yüklemek için öğe şablonunu özelleştirebilirsiniz, `My` derlemeye bir başvuru eklendiğinde ad alanı uzantısı. Sonuç olarak, kod dosyasını Visual Studio öğesi şablon olarak dışarı aktardığınızda, bu bütünleştirilmiş kod başvurusu hariç tutmak isteyeceksiniz.

## <a name="customize-the-item-template"></a>Öğe şablonu özelleştirme

Öğe şablonu, gelen yönetilecek etkinleştirebilirsiniz **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa. Belirtilen bir derlemeye başvuru için bir proje eklendiğinde, otomatik olarak eklenecek öğe şablonu da etkinleştirebilirsiniz. Özelleştirmeleri etkinleştirmek için CustomData dosyasına, şablonunuzu adlı yeni bir dosya ekleyin ve ardından yeni bir öğe, .vstemplate dosyasında XML ekleyin.

### <a name="add-the-customdata-file"></a>CustomData dosyası ekleme

CustomData dosyanın dosya adı uzantısına sahip bir metin dosyasıdır. CustomData (dosya adı ayarlanabilir herhangi bir değere şablonunuza anlamlı) ve XML içeren. CustomData dosyasındaki XML dahil etmek için Visual Basic bildirir, `My` kullanıcılar kullandığında uzantısı **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa. İsteğe bağlı olarak ekleyebilirsiniz <`AssemblyFullName>` CustomData dosyanızı XML özniteliği. Bu özel otomatik olarak yüklemek için Visual Basic bildirir `My` uzantısı, belirli bir derleme için bir başvuru olduğunda, projeye eklenir. CustomData dosyası oluşturmak için herhangi bir metin düzenleyicisi veya XML Düzenleyicisi'ni kullanın ve ardından, öğe şablonunun sıkıştırılmış klasöre (.zip dosyası) ekleyin.

Örneğin, aşağıdaki XML şablonu öğesi Visual Basic projesinde başvuru olduğunda Microsoft.VisualBasic.PowerPacks.Vs.dll derlemeye My uzantılarını klasörünün ekleyeceğiniz CustomData dosyasının içeriğini projeye eklenen gösterir.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

CustomData dosyayı içeren bir <`VBMyExtensionTemplate>` öğesinin aşağıdaki tabloda listelendiği gibi özniteliklere sahip.

|Öznitelik|Açıklama|
|---|---|
|`ID`|Gerekli. Uzantı için benzersiz bir tanımlayıcı. Bu Kimliğine sahip uzantı projesine eklenen, kullanıcı yeniden eklemek için istenmez.|
|`Version`|Gerekli. Öğe şablonu için bir sürüm numarası.|
|`AssemblyFullName`|İsteğe bağlı. Bir bütünleştirilmiş kod adı. Eklemek için bu derlemeye bir başvuru projeye eklendiğinde, kullanıcıdan istenir `My` bu öğe şablonu uzantı.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Ekleme \<CustomDataSignature > .vstemplate dosyasının öğesi

Visual Studio öğesi şablonunuzu olarak tanımlamak için bir `My` ad alanı uzantısı da, öğe şablonu için .vstemplate dosyasını değiştirmeniz gerekir. Eklemelisiniz bir `<CustomDataSignature>` öğesine `<TemplateData>` öğesi. `<CustomDataSignature>` Öğesi metni içermelidir `Microsoft.VisualBasic.MyExtension`, aşağıdaki örnekte gösterildiği gibi.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Bir sıkıştırılmış (.zip dosyası) klasördeki dosyaları doğrudan değişiklik yapamazsınız. .Vstemplate dosyası sıkıştırılmış bir klasörden kopyalayın değiştirin ve ardından sıkıştırılmış klasörü .vstemplate dosyasında, güncelleştirilmiş kopyayla gerekir.

Aşağıdaki örnek, sahip bir .vstemplate dosyasının içeriğini gösterir `<CustomDataSignature>` öğesi eklendi.

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a>Şablon yükle

Şablon yüklemek için sıkıştırılmış klasöre kopyalayabilirsiniz (*.zip* dosyası) için Visual Basic öğe şablonları klasörü. Kullanıcı öğe şablonları bulunan varsayılan olarak, *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ItemTemplates\Visual temel*. Alternatif olarak, şablon olarak bir Visual Studio yükleyicisi yayımlayabilirsiniz (*.vsi*) dosyası.

## <a name="see-also"></a>Ayrıca bkz.

- [Genişletme Visual Basic'te My Namespace](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Visual Basic Uygulama Modelini Genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
