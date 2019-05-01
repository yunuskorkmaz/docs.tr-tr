---
title: Paketleme ve özel My uzantılarını (Visual Basic) dağıtma
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014212"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="036f5-102">Paketleme ve özel My uzantılarını (Visual Basic) dağıtma</span><span class="sxs-lookup"><span data-stu-id="036f5-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="036f5-103">Visual Basic özel dağıtmanız için kolay bir yol sağlar `My` Visual Studio şablonları kullanarak ad alanı uzantıları.</span><span class="sxs-lookup"><span data-stu-id="036f5-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="036f5-104">Kendisi için bir proje şablonu oluşturuyorsanız, sizin `My` uzantıları bütünleyici yeni proje türünü, yalnızca kendi özel içerebilir `My` proje şablonu dışarı aktardığınızda uzantı kodu.</span><span class="sxs-lookup"><span data-stu-id="036f5-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="036f5-105">Proje şablonları dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="036f5-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="036f5-106">Varsa özel `My` uzantısıdır tek bir kod dosyasında, dosyanın her türden Visual Basic proje kullanıcıları ekleyebileceğiniz öğe şablonu dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="036f5-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="036f5-107">Ardından ek özellikleri ve özel davranışı etkinleştirmek için öğe şablonu özelleştirebilir `My` Visual Basic projesinde uzantısı.</span><span class="sxs-lookup"><span data-stu-id="036f5-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="036f5-108">Bu özellikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="036f5-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="036f5-109">Kendi özel yönetmenize izin vererek `My` uzantısından **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa.</span><span class="sxs-lookup"><span data-stu-id="036f5-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="036f5-110">Özel otomatik olarak ekleme `My` uzantısı için belirtilen derlemeyi bir başvuru olduğunda, bir projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="036f5-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="036f5-111">Gizleme `My` uzantı öğesi şablonunda **Öğe Ekle** iletişim kutusunu listeden proje öğelerinin bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="036f5-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="036f5-112">Bu konuda bir özel paket anlatılmaktadır `My` uzantısı alanından yönetilebilir bir gizli öğe şablonu olarak **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa.</span><span class="sxs-lookup"><span data-stu-id="036f5-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="036f5-113">Özel `My` uzantısı eklenebilir otomatik olarak belirtilen bir derlemeye başvuru için bir proje eklendiğinde.</span><span class="sxs-lookup"><span data-stu-id="036f5-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="036f5-114">Oluşturma bir ad alanı uzantısı</span><span class="sxs-lookup"><span data-stu-id="036f5-114">Create a My namespace extension</span></span>

<span data-ttu-id="036f5-115">Bir dağıtım paketi için özel bir oluşturmanın ilk adımı `My` bir uzantısı olarak tek bir kod dosyası oluşturmak için uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="036f5-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="036f5-116">Ayrıntıları ve özel bir oluşturma hakkında yönergeler `My` uzantısı bkz [Visual Basic'te My Namespace genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="036f5-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="036f5-117">Dışarı aktarma bir öğe şablonu olarak ad alanı uzantısı</span><span class="sxs-lookup"><span data-stu-id="036f5-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="036f5-118">İçeren bir kod dosyası oluşturduktan sonra `My` ad alanı uzantısı için kod dosyasını Visual Studio öğesi şablon olarak dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="036f5-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="036f5-119">Bir dosya Visual Studio öğesi şablon olarak dışarı aktarma yönergeleri için bkz [nasıl yapılır: Öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="036f5-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="036f5-120">Varsa, `My` ad alanı uzantısı belirli bir derleme üzerinde bir bağımlılık içeriyor, otomatik olarak yüklemek için öğe şablonunu özelleştirebilirsiniz, `My` derlemeye bir başvuru eklendiğinde ad alanı uzantısı.</span><span class="sxs-lookup"><span data-stu-id="036f5-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="036f5-121">Sonuç olarak, kod dosyasını Visual Studio öğesi şablon olarak dışarı aktardığınızda, bu bütünleştirilmiş kod başvurusu hariç tutmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="036f5-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="036f5-122">Öğe şablonu özelleştirme</span><span class="sxs-lookup"><span data-stu-id="036f5-122">Customize the item template</span></span>

<span data-ttu-id="036f5-123">Öğe şablonu, gelen yönetilecek etkinleştirebilirsiniz **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa.</span><span class="sxs-lookup"><span data-stu-id="036f5-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="036f5-124">Belirtilen bir derlemeye başvuru için bir proje eklendiğinde, otomatik olarak eklenecek öğe şablonu da etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="036f5-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="036f5-125">Özelleştirmeleri etkinleştirmek için CustomData dosyasına, şablonunuzu adlı yeni bir dosya ekleyin ve ardından yeni bir öğe, .vstemplate dosyasında XML ekleyin.</span><span class="sxs-lookup"><span data-stu-id="036f5-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="036f5-126">CustomData dosyası ekleme</span><span class="sxs-lookup"><span data-stu-id="036f5-126">Add the CustomData file</span></span>

<span data-ttu-id="036f5-127">CustomData dosyanın dosya adı uzantısına sahip bir metin dosyasıdır. CustomData (dosya adı ayarlanabilir herhangi bir değere şablonunuza anlamlı) ve XML içeren.</span><span class="sxs-lookup"><span data-stu-id="036f5-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="036f5-128">CustomData dosyasındaki XML dahil etmek için Visual Basic bildirir, `My` kullanıcılar kullandığında uzantısı **My uzantılarını** Visual Basic Proje Tasarımcısı'nın sayfa.</span><span class="sxs-lookup"><span data-stu-id="036f5-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="036f5-129">İsteğe bağlı olarak ekleyebilirsiniz <`AssemblyFullName>` CustomData dosyanızı XML özniteliği.</span><span class="sxs-lookup"><span data-stu-id="036f5-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="036f5-130">Bu özel otomatik olarak yüklemek için Visual Basic bildirir `My` uzantısı, belirli bir derleme için bir başvuru olduğunda, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="036f5-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="036f5-131">CustomData dosyası oluşturmak için herhangi bir metin düzenleyicisi veya XML Düzenleyicisi'ni kullanın ve ardından, öğe şablonunun sıkıştırılmış klasöre (.zip dosyası) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="036f5-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="036f5-132">Örneğin, aşağıdaki XML şablonu öğesi Visual Basic projesinde başvuru olduğunda Microsoft.VisualBasic.PowerPacks.Vs.dll derlemeye My uzantılarını klasörünün ekleyeceğiniz CustomData dosyasının içeriğini projeye eklenen gösterir.</span><span class="sxs-lookup"><span data-stu-id="036f5-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="036f5-133">CustomData dosyayı içeren bir <`VBMyExtensionTemplate>` öğesinin aşağıdaki tabloda listelendiği gibi özniteliklere sahip.</span><span class="sxs-lookup"><span data-stu-id="036f5-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="036f5-134">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="036f5-134">Attribute</span></span>|<span data-ttu-id="036f5-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="036f5-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="036f5-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="036f5-136">Required.</span></span> <span data-ttu-id="036f5-137">Uzantı için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="036f5-137">A unique identifier for the extension.</span></span> <span data-ttu-id="036f5-138">Bu Kimliğine sahip uzantı projesine eklenen, kullanıcı yeniden eklemek için istenmez.</span><span class="sxs-lookup"><span data-stu-id="036f5-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="036f5-139">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="036f5-139">Required.</span></span> <span data-ttu-id="036f5-140">Öğe şablonu için bir sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="036f5-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="036f5-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="036f5-141">Optional.</span></span> <span data-ttu-id="036f5-142">Bir bütünleştirilmiş kod adı.</span><span class="sxs-lookup"><span data-stu-id="036f5-142">An assembly name.</span></span> <span data-ttu-id="036f5-143">Eklemek için bu derlemeye bir başvuru projeye eklendiğinde, kullanıcıdan istenir `My` bu öğe şablonu uzantı.</span><span class="sxs-lookup"><span data-stu-id="036f5-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="036f5-144">Ekleme \<CustomDataSignature > .vstemplate dosyasının öğesi</span><span class="sxs-lookup"><span data-stu-id="036f5-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="036f5-145">Visual Studio öğesi şablonunuzu olarak tanımlamak için bir `My` ad alanı uzantısı da, öğe şablonu için .vstemplate dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="036f5-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="036f5-146">Eklemelisiniz bir `<CustomDataSignature>` öğesine `<TemplateData>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="036f5-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="036f5-147">`<CustomDataSignature>` Öğesi metni içermelidir `Microsoft.VisualBasic.MyExtension`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="036f5-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="036f5-148">Bir sıkıştırılmış (.zip dosyası) klasördeki dosyaları doğrudan değişiklik yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="036f5-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="036f5-149">.Vstemplate dosyası sıkıştırılmış bir klasörden kopyalayın değiştirin ve ardından sıkıştırılmış klasörü .vstemplate dosyasında, güncelleştirilmiş kopyayla gerekir.</span><span class="sxs-lookup"><span data-stu-id="036f5-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="036f5-150">Aşağıdaki örnek, sahip bir .vstemplate dosyasının içeriğini gösterir `<CustomDataSignature>` öğesi eklendi.</span><span class="sxs-lookup"><span data-stu-id="036f5-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="036f5-151">Şablon yükle</span><span class="sxs-lookup"><span data-stu-id="036f5-151">Install the template</span></span>

<span data-ttu-id="036f5-152">Şablon yüklemek için sıkıştırılmış klasöre kopyalayabilirsiniz (*.zip* dosyası) için Visual Basic öğe şablonları klasörü.</span><span class="sxs-lookup"><span data-stu-id="036f5-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="036f5-153">Kullanıcı öğe şablonları bulunan varsayılan olarak, *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ItemTemplates\Visual temel*.</span><span class="sxs-lookup"><span data-stu-id="036f5-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="036f5-154">Alternatif olarak, şablon olarak bir Visual Studio yükleyicisi yayımlayabilirsiniz (*.vsi*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="036f5-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="036f5-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="036f5-155">See also</span></span>

- [<span data-ttu-id="036f5-156">Genişletme Visual Basic'te My Namespace</span><span class="sxs-lookup"><span data-stu-id="036f5-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="036f5-157">Visual Basic Uygulama Modelini Genişletme</span><span class="sxs-lookup"><span data-stu-id="036f5-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="036f5-158">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="036f5-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="036f5-159">My Extensions Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="036f5-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
