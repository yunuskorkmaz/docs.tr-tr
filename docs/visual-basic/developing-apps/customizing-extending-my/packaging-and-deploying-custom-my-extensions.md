---
description: 'Daha fazla bilgi edinin: özel uzantılarımı paketleme ve dağıtma (Visual Basic)'
title: Özel uzantılarımı paketleme ve dağıtma
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 7037cc72951fc5228ae47998f39dca3455bf57de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775415"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Özel uzantılarımı paketleme ve dağıtma (Visual Basic)

Visual Basic, `My` Visual Studio şablonlarını kullanarak özel ad alanı uzantılarınızı dağıtmanın kolay bir yolunu sunar. `My`Uzantılarınızın yeni proje türünün ayrılmaz bir parçası olduğu bir proje şablonu oluşturuyorsanız, `My` şablonu dışarı aktardığınızda yalnızca özel uzantı kodunuzu projeye dahil edebilirsiniz. Proje şablonlarını dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).

Özel `My` uzantınız tek bir kod dosyasında yer alıyorsa, dosyayı kullanıcıların herhangi bir Visual Basic projesi türüne ekleyebir öğe şablonu olarak dışarı aktarabilirsiniz. Daha sonra, `My` bir Visual Basic projesindeki özel uzantınızın ek özelliklerini ve davranışını etkinleştirmek için öğe şablonunu özelleştirebilirsiniz. Bu yetenekler şunları içerir:

- Kullanıcıların özel `My` uzantınızı Visual Basic projesi tasarımcısının **uzantılarım** sayfasından yönetmesine izin verme.

- `My`Bir projeye belirtilen derlemeye bir başvuru eklendiğinde özel uzantınızı otomatik olarak ekleme.

- `My` **Öğe Ekle** iletişim kutusunda uzantı öğesi şablonunu, proje öğeleri listesinde yer kalmayacak şekilde gizleme.

Bu konu başlığı altında, bir özel `My` uzantının, Visual Basic proje tasarımcısının **uzantılarım** sayfasından yönetilebilen gizli bir öğe şablonu olarak nasıl paketlenebileceği açıklanmaktadır. Özel `My` uzantı, bir projeye belirtilen bir derlemeye başvuru eklendiğinde otomatik olarak da eklenebilir.

## <a name="create-a-my-namespace-extension"></a>My Namespace uzantısı oluştur

Özel bir uzantı için dağıtım paketi oluşturmanın ilk adımı, `My` uzantıyı tek bir kod dosyası olarak oluşturmaktır. Özel bir uzantının nasıl oluşturulacağı hakkındaki ayrıntılar ve yönergeler için `My` bkz. [Visual Basic ad alanını genişletme](extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>My Namespace uzantısı bir öğe şablonu olarak dışarı aktar

Ad alanı uzantınızı içeren bir kod dosyasına sahip olduktan sonra `My` , kod dosyasını bir Visual Studio öğe şablonu olarak dışarı aktarabilirsiniz. Bir dosyayı Visual Studio öğe şablonu olarak dışa aktarma hakkında yönergeler için bkz. [nasıl yapılır: öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> `My`Ad alanı uzantınızın belirli bir derlemeye bağımlılığı varsa, `My` Bu derlemeye bir başvuru eklendiğinde öğe şablonunuzu, ad alanı uzantınızı otomatik olarak yükleyecek şekilde özelleştirebilirsiniz. Sonuç olarak, kod dosyasını Visual Studio öğe şablonu olarak dışa aktardığınızda bu derleme başvurusunu hariç tutmak isteyeceksiniz.

## <a name="customize-the-item-template"></a>Öğe şablonunu özelleştirme

Öğe şablonunuzun, Visual Basic proje Tasarımcısı ' nın **uzantılarım** sayfasından yönetilmesini sağlayabilirsiniz. Ayrıca, bir projeye belirtilen derlemeye yönelik bir başvuru eklendiğinde öğe şablonunun otomatik olarak eklenmesini de sağlayabilirsiniz. Bu özelleştirmeleri etkinleştirmek için şablonunuza CustomData dosyası olarak adlandırılan yeni bir dosya ekleyin ve ardından. vstemplate dosyanızdaki XML 'e yeni bir öğe ekleyin.

### <a name="add-the-customdata-file"></a>CustomData dosyasını ekleme

CustomData dosyası, dosya adı uzantısına sahip olan bir metin dosyasıdır. CustomData (dosya adı, şablonunuz için anlamlı olan herhangi bir değere ayarlanabilir) ve XML içerir. CustomData dosyasındaki XML, `My` kullanıcılar Visual Basic proje Tasarımcısı 'Nın **uzantılarım** sayfasını kullanırken uzantınızı içermesini Visual Basic söyler. İsteğe bağlı olarak, <`AssemblyFullName>` özniteliğini CustomData FILE XML dosyanıza ekleyebilirsiniz. Bu `My` , projeye belirli bir derlemeye yönelik bir başvuru eklendiğinde özel uzantınızı otomatik olarak yüklemesini Visual Basic söyler. Herhangi bir metin düzenleyicisini veya XML düzenleyicisini kullanarak CustomData dosyasını oluşturabilir ve ardından bunu öğe şablonunuzun sıkıştırılmış klasörüne (. zip dosyası) ekleyebilirsiniz.

Örneğin, aşağıdaki XML, projeye Microsoft.VisualBasic.PowerPacks.Vs.dll derlemesine bir başvuru eklendiğinde bir Visual Basic projesinin Uzantılar klasörüne şablon öğesi ekleyecek bir CustomData dosyasının içeriğini gösterir.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

CustomData dosyası, `VBMyExtensionTemplate>` Aşağıdaki tabloda listelendiği gibi özniteliklere sahip bir <öğesi içerir.

|Öznitelik|Açıklama|
|---|---|
|`ID`|Gereklidir. Uzantı için benzersiz bir tanımlayıcı. Bu KIMLIĞE sahip uzantı projeye zaten eklendiyse, kullanıcıdan yeniden eklemesi istenmez.|
|`Version`|Gereklidir. Öğe şablonu için sürüm numarası.|
|`AssemblyFullName`|İsteğe bağlı. Bütünleştirilmiş kod adı. Projeye bu derlemeye bir başvuru eklendiğinde, kullanıcıdan `My` uzantıyı bu öğe şablonundan eklemesi istenir.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>\<CustomDataSignature>Öğesini. vstemplate dosyasına ekleyin

Visual Studio öğe şablonunuzu bir `My` ad alanı uzantısı olarak tanımlamak için, öğe şablonunuz için. vstemplate dosyasını da değiştirmelisiniz. Öğesine bir öğesi eklemeniz gerekir `<CustomDataSignature>` `<TemplateData>` . `<CustomDataSignature>` `Microsoft.VisualBasic.MyExtension` Aşağıdaki örnekte gösterildiği gibi öğesi, metnini içermelidir.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Sıkıştırılmış bir klasördeki (. zip dosyası) dosyaları doğrudan değiştiremezsiniz. . Vstemplate dosyasını sıkıştırılmış klasörden kopyalamanız, dosyayı değiştirmeniz ve sonra sıkıştırılmış klasördeki. vstemplate dosyasını güncelleştirilmiş kopyanınızdan değiştirmeniz gerekir.

Aşağıdaki örnek, öğesinin eklendiği bir. vstemplate dosyasının içeriğini gösterir `<CustomDataSignature>` .

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

Şablonu yüklemek için sıkıştırılmış klasörü (*. zip* dosyası) Visual Basic öğesi şablonları klasörüne kopyalayabilirsiniz. Varsayılan olarak, Kullanıcı öğesi şablonları *\<Version\> %USERPROFILE%\k\studio \Templates\ıtemtemplates\visual Basic* dizininde bulunur. Alternatif olarak, şablonu bir Visual Studio Yükleyicisi (*. vsi*) dosyası olarak yayımlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te My Ad Alanını Genişletme](extending-the-my-namespace.md)
- [Visual Basic Uygulama Modelini Genişletme](extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
