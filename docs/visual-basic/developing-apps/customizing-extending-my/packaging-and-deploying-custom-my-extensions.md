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
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="fd8a8-102">Özel uzantılarımı paketleme ve dağıtma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd8a8-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="fd8a8-103">Visual Basic, Visual Studio şablonlarını kullanarak özel `My` ad alanı uzantılarınızı dağıtmanın kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="fd8a8-104">`My` uzantılarınızın yeni proje türünün ayrılmaz bir parçası olduğu bir proje şablonu oluşturuyorsanız, şablonu dışarı aktardığınızda yalnızca özel `My` uzantı kodunuzu projeye dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="fd8a8-105">Proje şablonlarını dışarı aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: proje şablonları oluşturma](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="fd8a8-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="fd8a8-106">Özel `My` uzantınız tek bir kod dosyasında yer alıyorsa, dosyayı kullanıcıların herhangi bir Visual Basic projesi türüne ekleyebir öğe şablonu olarak dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="fd8a8-107">Daha sonra, bir Visual Basic projesindeki özel `My` uzantınızın ek özelliklerini ve davranışını etkinleştirmek için öğe şablonunu özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="fd8a8-108">Bu yetenekler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="fd8a8-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="fd8a8-109">Kullanıcıların özel `My` uzantınızı Visual Basic proje tasarımcısının **uzantılarım** sayfasından yönetmesine izin verme.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="fd8a8-110">Bir projeye belirtilen derlemeye yönelik bir başvuru eklendiğinde özel `My` uzantınızı otomatik olarak ekleme.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="fd8a8-111">**Öğe Ekle** iletişim kutusundaki `My` uzantı öğesi şablonunu, proje öğeleri listesinde yer kalmayacak şekilde gizleme.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="fd8a8-112">Bu konuda, Visual Basic proje Tasarımcısı ' nın **uzantılarım** sayfasından yönetilebilen bir gizli öğe şablonu olarak özel bir `My` uzantısının nasıl paketlenebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="fd8a8-113">Özel `My` uzantısı, bir projeye belirtilen bir derlemeye başvuru eklendiğinde otomatik olarak da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="fd8a8-114">My Namespace uzantısı oluştur</span><span class="sxs-lookup"><span data-stu-id="fd8a8-114">Create a My namespace extension</span></span>

<span data-ttu-id="fd8a8-115">Özel bir `My` uzantısı için dağıtım paketi oluşturmanın ilk adımı, uzantıyı tek bir kod dosyası olarak oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="fd8a8-116">Özel `My` uzantısının nasıl oluşturulacağı hakkında ayrıntılar ve yönergeler için, bkz. [Visual Basic My Namespace The](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)ı.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="fd8a8-117">My Namespace uzantısı bir öğe şablonu olarak dışarı aktar</span><span class="sxs-lookup"><span data-stu-id="fd8a8-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="fd8a8-118">`My` ad alanı uzantınızı içeren bir kod dosyasına sahip olduktan sonra, kod dosyasını Visual Studio öğe şablonu olarak dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="fd8a8-119">Bir dosyayı Visual Studio öğe şablonu olarak dışa aktarma hakkında yönergeler için bkz. [nasıl yapılır: öğe şablonları oluşturma](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="fd8a8-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="fd8a8-120">`My` ad alanı uzantınızın belirli bir derlemeye bağımlılığı varsa, bu derlemeye yönelik bir başvuru eklendiğinde öğe şablonunuzu, `My` ad alanı uzantınızı otomatik olarak yükleyecek şekilde özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="fd8a8-121">Sonuç olarak, kod dosyasını Visual Studio öğe şablonu olarak dışa aktardığınızda bu derleme başvurusunu hariç tutmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="fd8a8-122">Öğe şablonunu özelleştirme</span><span class="sxs-lookup"><span data-stu-id="fd8a8-122">Customize the item template</span></span>

<span data-ttu-id="fd8a8-123">Öğe şablonunuzun, Visual Basic proje Tasarımcısı ' nın **uzantılarım** sayfasından yönetilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="fd8a8-124">Ayrıca, bir projeye belirtilen derlemeye yönelik bir başvuru eklendiğinde öğe şablonunun otomatik olarak eklenmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="fd8a8-125">Bu özelleştirmeleri etkinleştirmek için şablonunuza CustomData dosyası olarak adlandırılan yeni bir dosya ekleyin ve ardından. vstemplate dosyanızdaki XML 'e yeni bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="fd8a8-126">CustomData dosyasını ekleme</span><span class="sxs-lookup"><span data-stu-id="fd8a8-126">Add the CustomData file</span></span>

<span data-ttu-id="fd8a8-127">CustomData dosyası, dosya adı uzantısına sahip olan bir metin dosyasıdır. CustomData (dosya adı, şablonunuz için anlamlı olan herhangi bir değere ayarlanabilir) ve XML içerir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="fd8a8-128">CustomData dosyasındaki XML, kullanıcılar Visual Basic proje Tasarımcısı 'nın **uzantılarım** sayfasını kullandıklarında `My` uzantınızı Visual Basic söyler.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="fd8a8-129">İsteğe bağlı olarak, <`AssemblyFullName>` özniteliğini CustomData File XML dosyanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="fd8a8-130">Bu, projeye belirli bir derlemeye yönelik bir başvuru eklendiğinde özel `My` uzantınızı otomatik olarak yüklemesini Visual Basic söyler.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="fd8a8-131">Herhangi bir metin düzenleyicisini veya XML düzenleyicisini kullanarak CustomData dosyasını oluşturabilir ve ardından bunu öğe şablonunuzun sıkıştırılmış klasörüne (. zip dosyası) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="fd8a8-132">Örneğin, aşağıdaki XML, projeye Microsoft. VisualBasic. PowerPacks. vs. dll derlemesine yönelik bir başvuru eklendiğinde, şablon öğesini bir Visual Basic projesinin Uzantılar klasörüne ekleyecek bir CustomData dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="fd8a8-133">CustomData dosyası, aşağıdaki tabloda listelendiği gibi özniteliklere sahip bir <`VBMyExtensionTemplate>` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="fd8a8-134">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd8a8-134">Attribute</span></span>|<span data-ttu-id="fd8a8-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd8a8-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="fd8a8-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-136">Required.</span></span> <span data-ttu-id="fd8a8-137">Uzantı için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-137">A unique identifier for the extension.</span></span> <span data-ttu-id="fd8a8-138">Bu KIMLIĞE sahip uzantı projeye zaten eklendiyse, kullanıcıdan yeniden eklemesi istenmez.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="fd8a8-139">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-139">Required.</span></span> <span data-ttu-id="fd8a8-140">Öğe şablonu için sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="fd8a8-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-141">Optional.</span></span> <span data-ttu-id="fd8a8-142">Bütünleştirilmiş kod adı.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-142">An assembly name.</span></span> <span data-ttu-id="fd8a8-143">Projeye bu derlemeye bir başvuru eklendiğinde, kullanıcıdan `My` uzantısını bu öğe şablonundan eklemesi istenir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="fd8a8-144">\<CustomDataSignature > öğesini. vstemplate dosyasına ekleyin</span><span class="sxs-lookup"><span data-stu-id="fd8a8-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="fd8a8-145">Visual Studio öğe şablonunuzu bir `My` ad alanı uzantısı olarak tanımlamak için, öğe şablonunuz için. vstemplate dosyasını da değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="fd8a8-146">`<TemplateData>` öğesine bir `<CustomDataSignature>` öğesi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="fd8a8-147">`<CustomDataSignature>` öğesi, aşağıdaki örnekte gösterildiği gibi, metin `Microsoft.VisualBasic.MyExtension`içermelidir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="fd8a8-148">Sıkıştırılmış bir klasördeki (. zip dosyası) dosyaları doğrudan değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="fd8a8-149">. Vstemplate dosyasını sıkıştırılmış klasörden kopyalamanız, dosyayı değiştirmeniz ve sonra sıkıştırılmış klasördeki. vstemplate dosyasını güncelleştirilmiş kopyanınızdan değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="fd8a8-150">Aşağıdaki örnek, `<CustomDataSignature>` öğesi eklenmiş bir. vstemplate dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="fd8a8-151">Şablonu yükler</span><span class="sxs-lookup"><span data-stu-id="fd8a8-151">Install the template</span></span>

<span data-ttu-id="fd8a8-152">Şablonu yüklemek için sıkıştırılmış klasörü ( *. zip* dosyası) Visual Basic öğesi şablonları klasörüne kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="fd8a8-153">Varsayılan olarak, Kullanıcı öğesi şablonları *%USERPROFILE%\k\studio \<Version\>\Templates\ıtemtemplates\visual Basic*dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="fd8a8-154">Alternatif olarak, şablonu bir Visual Studio Yükleyicisi ( *. vsi*) dosyası olarak yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd8a8-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd8a8-155">See also</span></span>

- [<span data-ttu-id="fd8a8-156">Visual Basic ad alanını genişletme</span><span class="sxs-lookup"><span data-stu-id="fd8a8-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="fd8a8-157">Visual Basic Uygulama Modelini Genişletme</span><span class="sxs-lookup"><span data-stu-id="fd8a8-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="fd8a8-158">My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="fd8a8-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="fd8a8-159">My Extensions Sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="fd8a8-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
