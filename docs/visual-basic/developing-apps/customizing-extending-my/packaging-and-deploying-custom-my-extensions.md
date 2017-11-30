---
title: "Paketleme ve özel My Uzantıları (Visual Basic) dağıtma"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94a9ea977d0add14ae9f0c9a889b008b94610ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>Paketleme ve özel My Uzantıları (Visual Basic) dağıtma
Visual Basic, kendi özel dağıtmak kolay bir yol sağlar `My` Visual Studio şablonları kullanarak ad alanı uzantıları. Kendisi için bir proje şablonu oluşturuyorsanız, `My` uzantıları yeni proje türü ayrılmaz bir parçası, yalnızca kendi özel içerebilir `My` proje şablonu dışarı aktardığınızda uzantı kodu. Proje şablonları dışarı aktarma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).  
  
 Varsa özel `My` uzantısı tek kod dosyasında, kullanıcıların herhangi bir Visual Basic projesinde türüne ekleyebileceğiniz öğesi şablonu olarak dosyasını dışarı aktarabilirsiniz. Ardından ek yetenekler ve kendi özel davranışını etkinleştirmek için öğe şablonu özelleştirebilir `My` Visual Basic projesinde uzantısı. Bu özellikler şunları içerir:  
  
-   Kullanıcıların kendi özel yönetmesine izin vererek `My` uzantı **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası.  
  
-   Otomatik olarak kendi özel ekleme `My` uzantısı belirtilen derleme için bir başvuru olduğunda, projeye eklenir.  
  
-   Gizleme `My` uzantısı öğesi şablonunda **Öğe Ekle** iletişim kutusunu proje öğeleri listede bulunmayan.  
  
 Bu konuda bir özel için nasıl ele alınmıştır `My` uzantısı sunucudan yönetilebilir bir gizli öğe şablonu olarak **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası. Özel `My` uzantısı da eklenebilir otomatik olarak belirtilen derlemesine başvuru bir projeye eklendiğinde.  
  
## <a name="create-a-my-namespace-extension"></a>Oluşturma bir My ad uzantısı  
 Özel bir dağıtım paketi oluşturmanın ilk adımı `My` uzantısıdır uzantısı tek bir kod dosyası olarak oluşturmak için. Ayrıntılar ve özel bir oluşturma hakkında yönergeler `My` uzantısı bkz [Visual Basic'te My Namespace genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Dışarı aktarma bir öğe şablonu olarak My ad uzantısı  
 İçeren bir kod dosyası oluşturduktan sonra `My` ad alanı uzantı kodu dosyasını Visual Studio öğe şablon olarak dışarı aktarabilirsiniz. Bir dosyayı Visual Studio öğe şablon olarak dışarı aktarma hakkında daha fazla yönerge için bkz: [nasıl yapılır: öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).  
  
> [!NOTE]
>  Varsa, `My` ad alanı uzantı üzerinde belirli bir derleme bir bağımlılığa sahiptir, otomatik olarak yüklemek için öğe şablonu özelleştirebilirsiniz, `My` o derlemesine başvuru eklendiğinde ad alanı uzantı. Sonuç olarak, kod dosyasını Visual Studio öğe şablon olarak dışarı aktardığınızda o derleme başvurusu çıkarılacak isteyeceksiniz.  
  
## <a name="customize-the-item-template"></a>Öğe şablonunu özelleştirme  
 Gelen yönetilecek öğesi şablonunuzu etkinleştirebilirsiniz **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası. Belirtilen derlemesine başvuru bir projeye eklendiğinde, otomatik olarak eklenecek öğe şablonu de etkinleştirebilirsiniz. Bu özelleştirmeler etkinleştirmek için CustomData dosyasına, şablonunuzu adlı yeni bir dosya ekleyin ve ardından yeni bir öğesi için XML .vstemplate dosyanızda ekleyin.  
  
### <a name="add-the-customdata-file"></a>CustomData dosyası ekleme  
 CustomData dosyası bir dosya adı uzantısına sahip bir metin dosyasıdır. (Dosya adı ayarlanabilir herhangi bir değere şablonunuza anlamlı) CustomData ve XML içeriyor. CustomData dosyasındaki XML dahil etmek için Visual Basic bildirir, `My` kullanıcılar kullandığınızda uzantısı **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası. İsteğe bağlı olarak ekleyebileceğiniz <`AssemblyFullName>` CustomData dosyanızı XML özniteliği. Bu özel otomatik olarak yüklemek için Visual Basic bildirir `My` uzantısı belirli bir derleme için bir başvuru olduğunda, projeye eklenir. CustomData dosyasını oluşturmak için herhangi bir metin düzenleyicisi veya XML Düzenleyicisi'ni kullanın ve öğeyi şablonun sıkıştırılmış klasöre (.zip dosyası) ekleyin.  
  
 Örneğin, aşağıdaki XML şablonu öğesi Visual Basic projesinde Microsoft.VisualBasic.PowerPacks.Vs.dll derleme için bir başvuru olduğunda My uzantıları klasörüne ekleyeceksiniz CustomData dosyasının içeriğini projeye eklenen gösterir.  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 CustomData dosyasını içeren bir <`VBMyExtensionTemplate>` öğesinin aşağıdaki tabloda listelendiği gibi özniteliklere sahip.  
  
|Öznitelik|Açıklama|  
|---|---|  
|`ID`|Gerekli. Uzantı için benzersiz bir tanımlayıcı. Bu Kimliğe sahip uzantısı projeye eklenir, kullanıcının yeniden eklemek için istenmez.|  
|`Version`|Gerekli. Öğe şablonu için bir sürüm numarası.|  
|`AssemblyFullName`|İsteğe bağlı. Derleme adı. Eklemek için bu derlemesine başvuru projeye eklendiğinde, kullanıcı istenir `My` bu öğe şablondan uzantısı.|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Ekleme \<CustomDataSignature > .vstemplate dosyasına öğesi  
 Visual Studio öğe şablonunuzu olarak tanımlamak için bir `My` ad alanı uzantı .vstemplate dosyasını öğesi şablonunuz için aynı zamanda değiştirmeniz gerekir. Eklemelisiniz bir `<CustomDataSignature>` öğesine `<TemplateData>` öğesi. `<CustomDataSignature>` Öğesi metni içermelidir `Microsoft.VisualBasic.MyExtension`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Bir sıkıştırılmış (.zip dosyası) klasördeki dosyaları doğrudan değiştiremezsiniz. Sıkıştırılmış klasörden .vstemplate dosyasına kopyalayın, değiştirin ve ardından sıkıştırılmış klasörü .vstemplate dosyasında, güncelleştirilmiş kopyayla gerekir.  
  
 Aşağıdaki örnek sahip .vstemplate dosyasının içeriğini gösterir `<CustomDataSignature>` öğe eklendi.  
  
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
 Şablon yüklemek için Visual Basic öğe şablonları klasöre (örneğin, My Documents\Visual Studio 2008\Templates\Item Templates\Visual temel) sıkıştırılmış (.zip dosyası) klasör kopyalayabilirsiniz. Alternatif olarak, şablon bir Visual Studio Yükleyicisi (.vsi) dosyası olarak yayımlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletme Visual Basic'te My Namespace](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [Visual Basic uygulama modelini genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Özelleştirme hangi nesnelerin kullanılabilir olduğunu My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [My Extensions sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
