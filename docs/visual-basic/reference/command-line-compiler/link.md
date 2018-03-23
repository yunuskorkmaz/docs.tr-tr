---
title: -bağlantı (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4410818b43c0ab12f9488198fffbe4b0f2d89252
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-link-visual-basic"></a><span data-ttu-id="afbf7-102">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbf7-102">-link (Visual Basic)</span></span>
<span data-ttu-id="afbf7-103">Derleyici COM türü bilgileri belirtilen derlemelerde şu anda derlediğiniz proje kullanılabilir hale getirmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="afbf7-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afbf7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afbf7-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="afbf7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="afbf7-105">Arguments</span></span>  
  
|<span data-ttu-id="afbf7-106">Terim</span><span class="sxs-lookup"><span data-stu-id="afbf7-106">Term</span></span>|<span data-ttu-id="afbf7-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="afbf7-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="afbf7-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="afbf7-108">Required.</span></span> <span data-ttu-id="afbf7-109">Derleme dosya adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="afbf7-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="afbf7-110">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="afbf7-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afbf7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afbf7-111">Remarks</span></span>  
 <span data-ttu-id="afbf7-112">`-link` Seçeneği katıştırılmış türde bilgi içeren bir uygulama dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="afbf7-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="afbf7-113">Uygulamanın gömülü tür bilgileri çalışma zamanı derlemesine başvuru gerek kalmadan uygulama çalışma zamanı derlemesi türlerinde sonra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afbf7-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="afbf7-114">Çeşitli çalışma zamanı derleme sürümleri yayımladıysanız katıştırılmış tür bilgileri içeren uygulama derlenmesi gerek kalmadan çeşitli sürümleriyle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="afbf7-115">Bir örnek için bkz: [izlenecek yol: yönetilen derlemelerden türler katıştırma](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="afbf7-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="afbf7-116">Kullanarak `-link` COM birlikte çalışma ile çalışırken seçenek özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="afbf7-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="afbf7-117">Böylelikle, uygulamanızın artık hedef bilgisayarda birincil birlikte çalışma derlemesi (PIA) gerektirir COM türlerini eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="afbf7-118">`-link` Seçeneği elde edilen derlenmiş kod başvurulan birlikte çalışma derlemeye COM tür bilgilerini katıştırma derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="afbf7-119">COM türü CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="afbf7-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="afbf7-120">Sonuç olarak, uygulamanızı aynı CLSID değerlerine sahip aynı COM türlerini yüklü olduğu bir hedef bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afbf7-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="afbf7-121">Microsoft Office'i otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="afbf7-122">Office gibi uygulamalar genellikle farklı sürümleri arasında aynı CLSID değeri tutmak için uygulamanız başvurulan COM türlerini uzun .NET Framework 4 veya daha sonra hedef bilgisayarda yüklü olduğundan ve yöntemler, özellikler, uygulamanızın kullandığı gibi kullanabilirsiniz veya Başvurulan COM türlerinde dahil olaylar.</span><span class="sxs-lookup"><span data-stu-id="afbf7-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="afbf7-123">`-link` Seçeneği yalnızca arabirimleri, yapılar ve temsilciler katıştırır.</span><span class="sxs-lookup"><span data-stu-id="afbf7-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="afbf7-124">COM sınıfları katıştırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="afbf7-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afbf7-125">Kodunuzda katıştırılmış COM türünün bir örneğini oluştururken uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="afbf7-126">Coclass'ı kullanarak katıştırılmış COM türünün bir örneği oluşturulmaya çalışılırken bir hata neden olur.</span><span class="sxs-lookup"><span data-stu-id="afbf7-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="afbf7-127">Ayarlamak için `-link` seçeneğini [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], bir derleme başvurusu ekleyin ve ayarlayın `Embed Interop Types` özelliğine **doğru**.</span><span class="sxs-lookup"><span data-stu-id="afbf7-127">To set the `-link` option in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="afbf7-128">İçin varsayılan `Embed Interop Types` özelliği **false**.</span><span class="sxs-lookup"><span data-stu-id="afbf7-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="afbf7-129">Bir COM derlemesine (a derlemesi) bağlantısının kendisi başka bir COM derlemesine (derleme B) başvuruyor, aşağıdakilerden biri doğruysa B derlemesine bağlantı gerekir:</span><span class="sxs-lookup"><span data-stu-id="afbf7-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="afbf7-130">Derlemesi türünden bir türden devralır veya derleme B'deki bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="afbf7-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="afbf7-131">Alan, özellik, olay veya b derlemesinden dönüş türü veya parametresi türü olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="afbf7-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="afbf7-132">Kullanım [- LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="afbf7-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="afbf7-133">Gibi [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği `-link` derleyici seçeneği başvuruları sık kullanılan Vbc.rsp yanıt dosyası kullanan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler.</span><span class="sxs-lookup"><span data-stu-id="afbf7-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="afbf7-134">Kullanmak [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) derleyicinin Vbc.rsp dosya kullanmasını istemiyorsanız derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="afbf7-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="afbf7-135">Kısa formunu `-link` olan `-l`.</span><span class="sxs-lookup"><span data-stu-id="afbf7-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="afbf7-136">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="afbf7-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="afbf7-137">Aşağıdaki bölümlerde, genel türler birlikte çalışma türlerini katıştır uygulamalarında kullanma sınırlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="afbf7-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="afbf7-138">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="afbf7-138">Generic Interfaces</span></span>  
 <span data-ttu-id="afbf7-139">Birlikte çalışma bir derlemeden katıştırılmış genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="afbf7-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="afbf7-140">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="afbf7-141">Genel Parametreler türleri</span><span class="sxs-lookup"><span data-stu-id="afbf7-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="afbf7-142">Türü birlikte çalışma bir derlemeden katıştırılmış genel bir parametre türleri, dış bir derlemeden tür olan kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="afbf7-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="afbf7-143">Bu kısıtlama, arabirimler için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="afbf7-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="afbf7-144">Örneğin, göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi <xref:Microsoft.Office.Interop.Excel> derleme.</span><span class="sxs-lookup"><span data-stu-id="afbf7-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="afbf7-145">Birlikte çalışma türlerini kitaplık katıştırır, <xref:Microsoft.Office.Interop.Excel> derleme ve bir parametreye sahip genel bir tür, türü döndüren bir yöntem sunarsa <xref:Microsoft.Office.Interop.Excel.Range> arabirim, yöntem aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="afbf7-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="afbf7-146">Aşağıdaki örnekte, istemci kodu döndürür yöntemini çağırabilir <xref:System.Collections.IList> hatasız genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="afbf7-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="afbf7-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="afbf7-147">Example</span></span>  
 <span data-ttu-id="afbf7-148">Aşağıdaki komut satırını kaynak dosyasını derler `OfficeApp.vb` ve başvuru derlemelerden `COMData1.dll` ve `COMData2.dll` üretmek için `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="afbf7-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="afbf7-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afbf7-149">See Also</span></span>  
 [<span data-ttu-id="afbf7-150">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="afbf7-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="afbf7-151">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="afbf7-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="afbf7-152">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbf7-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="afbf7-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="afbf7-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="afbf7-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="afbf7-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [<span data-ttu-id="afbf7-155">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="afbf7-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="afbf7-156">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="afbf7-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
