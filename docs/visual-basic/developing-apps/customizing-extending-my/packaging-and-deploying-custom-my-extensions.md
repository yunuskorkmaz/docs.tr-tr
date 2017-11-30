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
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="3c7a1-102">Paketleme ve özel My Uzantıları (Visual Basic) dağıtma</span><span class="sxs-lookup"><span data-stu-id="3c7a1-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="3c7a1-103">Visual Basic, kendi özel dağıtmak kolay bir yol sağlar `My` Visual Studio şablonları kullanarak ad alanı uzantıları.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="3c7a1-104">Kendisi için bir proje şablonu oluşturuyorsanız, `My` uzantıları yeni proje türü ayrılmaz bir parçası, yalnızca kendi özel içerebilir `My` proje şablonu dışarı aktardığınızda uzantı kodu.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="3c7a1-105">Proje şablonları dışarı aktarma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="3c7a1-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>  
  
 <span data-ttu-id="3c7a1-106">Varsa özel `My` uzantısı tek kod dosyasında, kullanıcıların herhangi bir Visual Basic projesinde türüne ekleyebileceğiniz öğesi şablonu olarak dosyasını dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="3c7a1-107">Ardından ek yetenekler ve kendi özel davranışını etkinleştirmek için öğe şablonu özelleştirebilir `My` Visual Basic projesinde uzantısı.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="3c7a1-108">Bu özellikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3c7a1-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="3c7a1-109">Kullanıcıların kendi özel yönetmesine izin vererek `My` uzantı **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="3c7a1-110">Otomatik olarak kendi özel ekleme `My` uzantısı belirtilen derleme için bir başvuru olduğunda, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="3c7a1-111">Gizleme `My` uzantısı öğesi şablonunda **Öğe Ekle** iletişim kutusunu proje öğeleri listede bulunmayan.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="3c7a1-112">Bu konuda bir özel için nasıl ele alınmıştır `My` uzantısı sunucudan yönetilebilir bir gizli öğe şablonu olarak **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="3c7a1-113">Özel `My` uzantısı da eklenebilir otomatik olarak belirtilen derlemesine başvuru bir projeye eklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="3c7a1-114">Oluşturma bir My ad uzantısı</span><span class="sxs-lookup"><span data-stu-id="3c7a1-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="3c7a1-115">Özel bir dağıtım paketi oluşturmanın ilk adımı `My` uzantısıdır uzantısı tek bir kod dosyası olarak oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="3c7a1-116">Ayrıntılar ve özel bir oluşturma hakkında yönergeler `My` uzantısı bkz [Visual Basic'te My Namespace genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3c7a1-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="3c7a1-117">Dışarı aktarma bir öğe şablonu olarak My ad uzantısı</span><span class="sxs-lookup"><span data-stu-id="3c7a1-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="3c7a1-118">İçeren bir kod dosyası oluşturduktan sonra `My` ad alanı uzantı kodu dosyasını Visual Studio öğe şablon olarak dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="3c7a1-119">Bir dosyayı Visual Studio öğe şablon olarak dışarı aktarma hakkında daha fazla yönerge için bkz: [nasıl yapılır: öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="3c7a1-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c7a1-120">Varsa, `My` ad alanı uzantı üzerinde belirli bir derleme bir bağımlılığa sahiptir, otomatik olarak yüklemek için öğe şablonu özelleştirebilirsiniz, `My` o derlemesine başvuru eklendiğinde ad alanı uzantı.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="3c7a1-121">Sonuç olarak, kod dosyasını Visual Studio öğe şablon olarak dışarı aktardığınızda o derleme başvurusu çıkarılacak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="3c7a1-122">Öğe şablonunu özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3c7a1-122">Customize the item template</span></span>  
 <span data-ttu-id="3c7a1-123">Gelen yönetilecek öğesi şablonunuzu etkinleştirebilirsiniz **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="3c7a1-124">Belirtilen derlemesine başvuru bir projeye eklendiğinde, otomatik olarak eklenecek öğe şablonu de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="3c7a1-125">Bu özelleştirmeler etkinleştirmek için CustomData dosyasına, şablonunuzu adlı yeni bir dosya ekleyin ve ardından yeni bir öğesi için XML .vstemplate dosyanızda ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="3c7a1-126">CustomData dosyası ekleme</span><span class="sxs-lookup"><span data-stu-id="3c7a1-126">Add the CustomData file</span></span>  
 <span data-ttu-id="3c7a1-127">CustomData dosyası bir dosya adı uzantısına sahip bir metin dosyasıdır. (Dosya adı ayarlanabilir herhangi bir değere şablonunuza anlamlı) CustomData ve XML içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="3c7a1-128">CustomData dosyasındaki XML dahil etmek için Visual Basic bildirir, `My` kullanıcılar kullandığınızda uzantısı **My Extensions** Visual Basic Proje Tasarımcısı'nın sayfası.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="3c7a1-129">İsteğe bağlı olarak ekleyebileceğiniz <`AssemblyFullName>` CustomData dosyanızı XML özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="3c7a1-130">Bu özel otomatik olarak yüklemek için Visual Basic bildirir `My` uzantısı belirli bir derleme için bir başvuru olduğunda, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="3c7a1-131">CustomData dosyasını oluşturmak için herhangi bir metin düzenleyicisi veya XML Düzenleyicisi'ni kullanın ve öğeyi şablonun sıkıştırılmış klasöre (.zip dosyası) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="3c7a1-132">Örneğin, aşağıdaki XML şablonu öğesi Visual Basic projesinde Microsoft.VisualBasic.PowerPacks.Vs.dll derleme için bir başvuru olduğunda My uzantıları klasörüne ekleyeceksiniz CustomData dosyasının içeriğini projeye eklenen gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="3c7a1-133">CustomData dosyasını içeren bir <`VBMyExtensionTemplate>` öğesinin aşağıdaki tabloda listelendiği gibi özniteliklere sahip.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="3c7a1-134">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c7a1-134">Attribute</span></span>|<span data-ttu-id="3c7a1-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c7a1-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="3c7a1-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-136">Required.</span></span> <span data-ttu-id="3c7a1-137">Uzantı için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-137">A unique identifier for the extension.</span></span> <span data-ttu-id="3c7a1-138">Bu Kimliğe sahip uzantısı projeye eklenir, kullanıcının yeniden eklemek için istenmez.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="3c7a1-139">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-139">Required.</span></span> <span data-ttu-id="3c7a1-140">Öğe şablonu için bir sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="3c7a1-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-141">Optional.</span></span> <span data-ttu-id="3c7a1-142">Derleme adı.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-142">An assembly name.</span></span> <span data-ttu-id="3c7a1-143">Eklemek için bu derlemesine başvuru projeye eklendiğinde, kullanıcı istenir `My` bu öğe şablondan uzantısı.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="3c7a1-144">Ekleme \<CustomDataSignature > .vstemplate dosyasına öğesi</span><span class="sxs-lookup"><span data-stu-id="3c7a1-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="3c7a1-145">Visual Studio öğe şablonunuzu olarak tanımlamak için bir `My` ad alanı uzantı .vstemplate dosyasını öğesi şablonunuz için aynı zamanda değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="3c7a1-146">Eklemelisiniz bir `<CustomDataSignature>` öğesine `<TemplateData>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="3c7a1-147">`<CustomDataSignature>` Öğesi metni içermelidir `Microsoft.VisualBasic.MyExtension`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="3c7a1-148">Bir sıkıştırılmış (.zip dosyası) klasördeki dosyaları doğrudan değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="3c7a1-149">Sıkıştırılmış klasörden .vstemplate dosyasına kopyalayın, değiştirin ve ardından sıkıştırılmış klasörü .vstemplate dosyasında, güncelleştirilmiş kopyayla gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="3c7a1-150">Aşağıdaki örnek sahip .vstemplate dosyasının içeriğini gösterir `<CustomDataSignature>` öğe eklendi.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
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
  
## <a name="install-the-template"></a><span data-ttu-id="3c7a1-151">Şablon yükle</span><span class="sxs-lookup"><span data-stu-id="3c7a1-151">Install the template</span></span>  
 <span data-ttu-id="3c7a1-152">Şablon yüklemek için Visual Basic öğe şablonları klasöre (örneğin, My Documents\Visual Studio 2008\Templates\Item Templates\Visual temel) sıkıştırılmış (.zip dosyası) klasör kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="3c7a1-153">Alternatif olarak, şablon bir Visual Studio Yükleyicisi (.vsi) dosyası olarak yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7a1-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c7a1-154">See also</span></span>  
 [<span data-ttu-id="3c7a1-155">Genişletme Visual Basic'te My Namespace</span><span class="sxs-lookup"><span data-stu-id="3c7a1-155">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [<span data-ttu-id="3c7a1-156">Visual Basic uygulama modelini genişletme</span><span class="sxs-lookup"><span data-stu-id="3c7a1-156">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [<span data-ttu-id="3c7a1-157">Özelleştirme hangi nesnelerin kullanılabilir olduğunu My</span><span class="sxs-lookup"><span data-stu-id="3c7a1-157">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [<span data-ttu-id="3c7a1-158">My Extensions sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="3c7a1-158">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
