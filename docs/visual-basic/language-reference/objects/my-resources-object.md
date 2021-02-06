---
description: ': My. Resources nesnesi hakkında daha fazla bilgi edinin'
title: My.Resources Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ecd8e79aacea85080dc341ae36b362a595893034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640634"
---
# <a name="myresources-object"></a><span data-ttu-id="b1f4f-103">My.Resources Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b1f4f-103">My.Resources Object</span></span>

<span data-ttu-id="b1f4f-104">Uygulamanın kaynaklarına erişmek için özellikler ve sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-104">Provides properties and classes for accessing the application's resources.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1f4f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1f4f-105">Remarks</span></span>  

 <span data-ttu-id="b1f4f-106">`My.Resources`Nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-106">The `My.Resources` object provides access to the application's resources and lets you dynamically retrieve resources for your application.</span></span> <span data-ttu-id="b1f4f-107">Daha fazla bilgi için bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b1f4f-107">For more information, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
 <span data-ttu-id="b1f4f-108">`My.Resources`Nesne yalnızca genel kaynakları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="b1f4f-109">Formlarla ilişkili kaynak dosyalarına erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="b1f4f-110">Form kaynaklarına formdan erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="b1f4f-111">Uygulamanın kültüre özgü kaynak dosyalarına `My.Resources` nesnesinden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-111">You can access the application's culture-specific resource files from the `My.Resources` object.</span></span> <span data-ttu-id="b1f4f-112">Varsayılan olarak, `My.Resources` nesnesi kaynak dosyasındaki, özelliğindeki kültür ile eşleşen kaynakları arar <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-112">By default, the `My.Resources` object looks up resources from the resource file that matches the culture in the <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> property.</span></span> <span data-ttu-id="b1f4f-113">Ancak, bu davranışı geçersiz kılabilir ve kaynaklar için kullanmak üzere belirli bir kültür belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-113">However, you can override this behavior and specify a particular culture to use for the resources.</span></span> <span data-ttu-id="b1f4f-114">Daha fazla bilgi için bkz. [Masaüstü uygulamalarındaki kaynaklar](../../../framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="b1f4f-114">For more information, see [Resources in Desktop Apps](../../../framework/resources/index.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1f4f-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b1f4f-115">Properties</span></span>  

 <span data-ttu-id="b1f4f-116">Nesnesinin özellikleri, `My.Resources` uygulamanızın kaynaklarına salt okuma erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-116">The properties of the `My.Resources` object provide read-only access to your application's resources.</span></span> <span data-ttu-id="b1f4f-117">Kaynak eklemek veya kaldırmak için, **Proje tasarımcısını** kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-117">To add or remove resources, use the **Project Designer**.</span></span> <span data-ttu-id="b1f4f-118">ResourceName kullanarak **Proje Tasarımcısı** aracılığıyla eklenen kaynaklara erişebilirsiniz `My.Resources.` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-118">You can access resources added through the **Project Designer** by using `My.Resources.`*resourceName*.</span></span>  
  
 <span data-ttu-id="b1f4f-119">Ayrıca, **Çözüm Gezgini** ' de projenizi seçip **Yeni öğe Ekle ' ye** tıklayarak veya **Proje** menüsünden **Varolan öğe** Ekle ' yi seçerek kaynak dosyalarını ekleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-119">You can also add or remove resource files by selecting your project in **Solution Explorer** and clicking **Add New Item** or **Add Existing Item** from the **Project** menu.</span></span> <span data-ttu-id="b1f4f-120">`My.Resources.` *ResourceFileName* `.` *resourceName* kullanarak bu şekilde eklenen kaynaklara erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-120">You can access resources added in this manner by using `My.Resources.`*resourceFileName*`.`*resourceName*.</span></span>  
  
 <span data-ttu-id="b1f4f-121">Her kaynağın bir adı, kategorisi ve değeri vardır ve bu kaynak ayarları, kaynağa erişme özelliğinin nesnede nasıl göründüğünü belirlenir `My.Resources` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-121">Each resource has a name, category, and value, and these resource settings determine how the property to access the resource appears in the `My.Resources` object.</span></span> <span data-ttu-id="b1f4f-122">**Proje Tasarımcısı**'nda eklenen kaynaklar için:</span><span class="sxs-lookup"><span data-stu-id="b1f4f-122">For resources added in the **Project Designer**:</span></span>  
  
- <span data-ttu-id="b1f4f-123">Ad, özelliğin adını belirler,</span><span class="sxs-lookup"><span data-stu-id="b1f4f-123">The name determines the name of the property,</span></span>  
  
- <span data-ttu-id="b1f4f-124">Kaynak verileri, özelliğinin değeridir,</span><span class="sxs-lookup"><span data-stu-id="b1f4f-124">The resource data is the value of the property,</span></span>  
  
- <span data-ttu-id="b1f4f-125">Kategori, özelliğin türünü belirler:</span><span class="sxs-lookup"><span data-stu-id="b1f4f-125">The category determines the type of the property:</span></span>  
  
|<span data-ttu-id="b1f4f-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="b1f4f-126">Category</span></span>|<span data-ttu-id="b1f4f-127">Özellik veri türü</span><span class="sxs-lookup"><span data-stu-id="b1f4f-127">Property data type</span></span>|  
|---|---|  
|<span data-ttu-id="b1f4f-128">**Dizeler**</span><span class="sxs-lookup"><span data-stu-id="b1f4f-128">**Strings**</span></span>|[<span data-ttu-id="b1f4f-129">Dize</span><span class="sxs-lookup"><span data-stu-id="b1f4f-129">String</span></span>](../data-types/string-data-type.md)|  
|<span data-ttu-id="b1f4f-130">**Görüntüler**</span><span class="sxs-lookup"><span data-stu-id="b1f4f-130">**Images**</span></span>|<xref:System.Drawing.Bitmap>|  
|<span data-ttu-id="b1f4f-131">**Simgeler**</span><span class="sxs-lookup"><span data-stu-id="b1f4f-131">**Icons**</span></span>|<xref:System.Drawing.Icon>|  
|<span data-ttu-id="b1f4f-132">**Ses**</span><span class="sxs-lookup"><span data-stu-id="b1f4f-132">**Audio**</span></span>|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <span data-ttu-id="b1f4f-133"><xref:System.IO.UnmanagedMemoryStream>Sınıfı sınıfından türetilir, bu <xref:System.IO.Stream> nedenle, yöntemi gibi akışlar alan yöntemlerle kullanılabilir <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-133">The <xref:System.IO.UnmanagedMemoryStream> class derives from the <xref:System.IO.Stream> class, so it can be used with methods that take streams, such as the <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> method.</span></span>|  
|<span data-ttu-id="b1f4f-134">**Dosyalar**</span><span class="sxs-lookup"><span data-stu-id="b1f4f-134">**Files**</span></span>|<span data-ttu-id="b1f4f-135">-   Metin dosyaları için [dize](../data-types/string-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-135">-   [String](../data-types/string-data-type.md) for text files.</span></span><br /><span data-ttu-id="b1f4f-136">-   <xref:System.Drawing.Bitmap> görüntü dosyaları için.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-136">-   <xref:System.Drawing.Bitmap> for image files.</span></span><br /><span data-ttu-id="b1f4f-137">-   <xref:System.Drawing.Icon> simge dosyaları için.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-137">-   <xref:System.Drawing.Icon> for icon files.</span></span><br /><span data-ttu-id="b1f4f-138">-   <xref:System.IO.UnmanagedMemoryStream> ses dosyaları için.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-138">-   <xref:System.IO.UnmanagedMemoryStream> for sound files.</span></span>|  
|<span data-ttu-id="b1f4f-139">**Diğer**</span><span class="sxs-lookup"><span data-stu-id="b1f4f-139">**Other**</span></span>|<span data-ttu-id="b1f4f-140">Tasarımcının **tür** sütunundaki bilgiler tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-140">Determined by the information in the designer's **Type** column.</span></span>|  
  
## <a name="classes"></a><span data-ttu-id="b1f4f-141">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b1f4f-141">Classes</span></span>  

 <span data-ttu-id="b1f4f-142">`My.Resources`Nesnesi, her kaynak dosyasını paylaşılan özelliklere sahip bir sınıf olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-142">The `My.Resources` object exposes each resource file as a class with shared properties.</span></span> <span data-ttu-id="b1f4f-143">Sınıf adı, kaynak dosyasının adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-143">The class name is the same as the name of the resource file.</span></span> <span data-ttu-id="b1f4f-144">Önceki bölümde açıklandığı gibi, bir kaynak dosyasındaki kaynaklar sınıfında Özellikler olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-144">As described in the previous section, the resources in a resource file are exposed as properties in the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f4f-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f4f-145">Example</span></span>  

 <span data-ttu-id="b1f4f-146">Bu örnek, bir formun başlığını uygulama kaynak dosyasında adlı dize kaynağına ayarlar `Form1Title` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-146">This example sets the title of a form to the string resource named `Form1Title` in the application resource file.</span></span> <span data-ttu-id="b1f4f-147">Örneğin çalışması için, uygulamanın kaynak dosyasında adlı bir dize olması gerekir `Form1Title` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-147">For the example to work, the application must have a string named `Form1Title` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b1f4f-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f4f-148">Example</span></span>  

 <span data-ttu-id="b1f4f-149">Bu örnek, formun simgesini `Form1Icon` uygulamanın kaynak dosyasında saklanan adlı simgeye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-149">This example sets the icon of the form to the icon named `Form1Icon` that is stored in the application's resource file.</span></span> <span data-ttu-id="b1f4f-150">Örneğin çalışması için, uygulamanın kaynak dosyasında adında bir simge olması gerekir `Form1Icon` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-150">For the example to work, the application must have an icon named `Form1Icon` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b1f4f-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f4f-151">Example</span></span>  

 <span data-ttu-id="b1f4f-152">Bu örnek, bir formun arka plan görüntüsünü, `Form1Background` uygulama kaynak dosyasında olan adlı görüntü kaynağı olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-152">This example sets the background image of a form to the image resource named `Form1Background`, which is in the application resource file.</span></span> <span data-ttu-id="b1f4f-153">Bu örneğin çalışması için, uygulamanın kaynak dosyasında adlı bir görüntü kaynağı olması gerekir `Form1Background` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-153">For this example to work, the application must have an image resource named `Form1Background` in its resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b1f4f-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f4f-154">Example</span></span>  

 <span data-ttu-id="b1f4f-155">Bu örnek `Form1Greeting` , uygulamanın kaynak dosyasında adlı bir ses kaynağı olarak depolanan sesi çalar.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-155">This example plays the sound that is stored as an audio resource named `Form1Greeting` in the application's resource file.</span></span> <span data-ttu-id="b1f4f-156">Örneğin çalışması için, uygulamanın kaynak dosyasında adlı bir ses kaynağı olmalıdır `Form1Greeting` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-156">For the example to work, the application must have an audio resource named `Form1Greeting` in its resource file.</span></span> <span data-ttu-id="b1f4f-157">`My.Computer.Audio.Play`Yöntemi yalnızca Windows Forms uygulamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-157">The `My.Computer.Audio.Play` method is available only for Windows Forms applications.</span></span>  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b1f4f-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f4f-158">Example</span></span>  

 <span data-ttu-id="b1f4f-159">Bu örnekte, uygulamanın dize kaynağının Fransızca-kültür sürümü alınır.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-159">This example retrieves the French-culture version of a  string resource of the application.</span></span> <span data-ttu-id="b1f4f-160">Kaynak adı `Message` .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-160">The resource is named `Message`.</span></span> <span data-ttu-id="b1f4f-161">Nesnenin kullandığı kültürü değiştirmek için `My.Resources` , örnek kullanılır <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .</span><span class="sxs-lookup"><span data-stu-id="b1f4f-161">To change the culture that the `My.Resources` object uses, the example uses <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</span></span>  
  
 <span data-ttu-id="b1f4f-162">Bu örneğin çalışması için, uygulamanın kaynak dosyasında adında bir dize olması `Message` ve uygulamanın, Resources.fr-fr. resx kaynak dosyasının Fransızca-kültür sürümüne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-162">For this example to work, the application must have a string named `Message` in its resource file, and the application should have the French-culture version of that resource file, Resources.fr-FR.resx.</span></span> <span data-ttu-id="b1f4f-163">Uygulamanın, kaynak dosyasının Fransızca-kültür sürümü yoksa, `My.Resource` nesne kaynağı varsayılan kültür kaynak dosyasından alır.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-163">If the application does not have the French-culture version of the resource file, the `My.Resource` object retrieves the resource from the default-culture resource file.</span></span>  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="b1f4f-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f4f-164">See also</span></span>

- [<span data-ttu-id="b1f4f-165">Uygulama Kaynaklarını Yönetme (.NET)</span><span class="sxs-lookup"><span data-stu-id="b1f4f-165">Managing Application Resources (.NET)</span></span>](/visualstudio/ide/managing-application-resources-dotnet)
- [<span data-ttu-id="b1f4f-166">Masaüstü uygulamalarındaki kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b1f4f-166">Resources in Desktop Apps</span></span>](../../../framework/resources/index.md)
