---
title: Özel uzantılarımı paketleme ve dağıtma
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330255"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Özel uzantılarımı paketleme ve dağıtma (Visual Basic)

Visual Basic, Visual Studio şablonlarını kullanarak özel `My` ad alanı uzantılarınızı dağıtmanın kolay bir yolunu sunar. Uzantılarınızın `My` yeni proje türünün ayrılmaz bir parçası olduğu bir proje şablonu oluşturuyorsanız, şablonu dışarı aktardığınızda yalnızca özel `My` uzantı kodunuzu projeye dahil edebilirsiniz. Proje şablonlarını dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).

Özel `My` uzantınız tek bir kod dosyasında yer alıyorsa, dosyayı kullanıcıların herhangi bir Visual Basic projesi türüne ekleyebir öğe şablonu olarak dışarı aktarabilirsiniz. Daha sonra, bir Visual Basic projesindeki özel `My` uzantınızın ek özelliklerini ve davranışını etkinleştirmek için öğe şablonunu özelleştirebilirsiniz. Bu yetenekler şunları içerir:

- Kullanıcıların özel `My` uzantınızı Visual Basic projesi tasarımcısının **uzantılarım** sayfasından yönetmesine izin verme.

- Bir projeye belirtilen derlemeye `My` bir başvuru eklendiğinde özel uzantınızı otomatik olarak ekleme.

- `My` **Öğe Ekle** iletişim kutusunda uzantı öğesi şablonunu, proje öğeleri listesinde yer kalmayacak şekilde gizleme.

Bu konu başlığı altında, bir özel `My` uzantının, Visual Basic proje tasarımcısının **uzantılarım** sayfasından yönetilebilen gizli bir öğe şablonu olarak nasıl paketlenebileceği açıklanmaktadır. Özel `My` uzantı, bir projeye belirtilen bir derlemeye başvuru eklendiğinde otomatik olarak da eklenebilir.

## <a name="create-a-my-namespace-extension"></a>My Namespace uzantısı oluştur

Özel `My` bir uzantı için dağıtım paketi oluşturmanın ilk adımı, uzantıyı tek bir kod dosyası olarak oluşturmaktır. Özel `My` bir uzantının nasıl oluşturulacağı hakkındaki ayrıntılar ve yönergeler için bkz. [Visual Basic ad alanını genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>My Namespace uzantısı bir öğe şablonu olarak dışarı aktar

Ad alanı uzantınızı `My` içeren bir kod dosyasına sahip olduktan sonra, kod dosyasını bir Visual Studio öğe şablonu olarak dışarı aktarabilirsiniz. Bir dosyayı Visual Studio öğe şablonu olarak dışa aktarma hakkında yönergeler için bkz. [nasıl yapılır: öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Ad alanı `My` uzantınızın belirli bir derlemeye bağımlılığı varsa, bu derlemeye bir başvuru eklendiğinde öğe şablonunuzu, ad alanı uzantınızı `My` otomatik olarak yükleyecek şekilde özelleştirebilirsiniz. Sonuç olarak, kod dosyasını Visual Studio öğe şablonu olarak dışa aktardığınızda bu derleme başvurusunu hariç tutmak isteyeceksiniz.

## <a name="customize-the-item-template"></a>Öğe şablonunu özelleştirme

Öğe şablonunuzun, Visual Basic proje Tasarımcısı ' nın **uzantılarım** sayfasından yönetilmesini sağlayabilirsiniz. Ayrıca, bir projeye belirtilen derlemeye yönelik bir başvuru eklendiğinde öğe şablonunun otomatik olarak eklenmesini de sağlayabilirsiniz. Bu özelleştirmeleri etkinleştirmek için şablonunuza CustomData dosyası olarak adlandırılan yeni bir dosya ekleyin ve ardından. vstemplate dosyanızdaki XML 'e yeni bir öğe ekleyin.

### <a name="add-the-customdata-file"></a>CustomData dosyasını ekleme

CustomData dosyası, dosya adı uzantısına sahip olan bir metin dosyasıdır. CustomData (dosya adı, şablonunuz için anlamlı olan herhangi bir değere ayarlanabilir) ve XML içerir. CustomData dosyasındaki XML, kullanıcılar Visual Basic proje Tasarımcısı 'nın `My` **uzantılarım** sayfasını kullanırken uzantınızı içermesini Visual Basic söyler. İsteğe bağlı olarak, <`AssemblyFullName>` özniteliğini CustomData File XML dosyanıza ekleyebilirsiniz. Bu, projeye belirli bir derlemeye yönelik bir `My` başvuru eklendiğinde özel uzantınızı otomatik olarak yüklemesini Visual Basic söyler. Herhangi bir metin düzenleyicisini veya XML düzenleyicisini kullanarak CustomData dosyasını oluşturabilir ve ardından bunu öğe şablonunuzun sıkıştırılmış klasörüne (. zip dosyası) ekleyebilirsiniz.

Örneğin, aşağıdaki XML, projeye Microsoft. VisualBasic. PowerPacks. vs. dll derlemesine yönelik bir başvuru eklendiğinde, şablon öğesini bir Visual Basic projesinin Uzantılar klasörüne ekleyecek bir CustomData dosyasının içeriğini gösterir.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

CustomData dosyası, aşağıdaki tabloda listelendiği `VBMyExtensionTemplate>` gibi özniteliklere sahip bir <öğesi içerir.

|Öznitelik|Açıklama|
|---|---|
|`ID`|Gereklidir. Uzantı için benzersiz bir tanımlayıcı. Bu KIMLIĞE sahip uzantı projeye zaten eklendiyse, kullanıcıdan yeniden eklemesi istenmez.|
|`Version`|Gereklidir. Öğe şablonu için sürüm numarası.|
|`AssemblyFullName`|İsteğe bağlı. Bütünleştirilmiş kod adı. Projeye bu derlemeye bir başvuru eklendiğinde, kullanıcıdan `My` uzantıyı bu öğe şablonundan eklemesi istenir.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>\<CustomDataSignature> öğesini. vstemplate dosyasına ekleyin

Visual Studio öğe şablonunuzu bir `My` ad alanı uzantısı olarak tanımlamak için, öğe şablonunuz için. vstemplate dosyasını da değiştirmelisiniz. Öğesine bir `<CustomDataSignature>` öğesi `<TemplateData>` eklemeniz gerekir. Aşağıdaki `<CustomDataSignature>` örnekte gösterildiği gibi öğesi, `Microsoft.VisualBasic.MyExtension`metnini içermelidir.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Sıkıştırılmış bir klasördeki (. zip dosyası) dosyaları doğrudan değiştiremezsiniz. . Vstemplate dosyasını sıkıştırılmış klasörden kopyalamanız, dosyayı değiştirmeniz ve sonra sıkıştırılmış klasördeki. vstemplate dosyasını güncelleştirilmiş kopyanınızdan değiştirmeniz gerekir.

Aşağıdaki örnek, `<CustomDataSignature>` öğesinin eklendiği bir. vstemplate dosyasının içeriğini gösterir.

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

## <a name="install-the-template"></a>Şablonu yükler

Şablonu yüklemek için sıkıştırılmış klasörü (*. zip* dosyası) Visual Basic öğesi şablonları klasörüne kopyalayabilirsiniz. Varsayılan olarak, Kullanıcı öğesi şablonları *%USERPROFILE%\k\studio \<\>Version \Templates\ıtemtemplates\visual Basic*dizininde bulunur. Alternatif olarak, şablonu bir Visual Studio Yükleyicisi (*. vsi*) dosyası olarak yayımlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te My Ad Alanını Genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Visual Basic Uygulama Modelini Genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
