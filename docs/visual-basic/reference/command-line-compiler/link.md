---
title: -bağlantı (Visual Basic)
ms.date: 03/10/2018
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
ms.openlocfilehash: fbce22755b3732896a226c00bbf8e068dc1f098e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929391"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="a4da1-102">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4da1-102">-link (Visual Basic)</span></span>
<span data-ttu-id="a4da1-103">Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4da1-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4da1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4da1-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4da1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a4da1-105">Arguments</span></span>  
  
|<span data-ttu-id="a4da1-106">Terim</span><span class="sxs-lookup"><span data-stu-id="a4da1-106">Term</span></span>|<span data-ttu-id="a4da1-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="a4da1-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="a4da1-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a4da1-108">Required.</span></span> <span data-ttu-id="a4da1-109">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="a4da1-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="a4da1-110">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="a4da1-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4da1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4da1-111">Remarks</span></span>  
 <span data-ttu-id="a4da1-112">`-link` Seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4da1-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="a4da1-113">Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="a4da1-114">Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="a4da1-115">Bir örnek için bkz [. İzlenecek yol: Yönetilen derlemelerden](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)türler ekleme.</span><span class="sxs-lookup"><span data-stu-id="a4da1-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>  
  
 <span data-ttu-id="a4da1-116">`-link` Seçeneğinin kullanılması özellikle com birlikte çalışabilirliğine çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4da1-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="a4da1-117">Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4da1-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="a4da1-118">`-link` Seçeneği, derleyicinin başvurulan birlikte çalışma derlemesindeki com tür bilgilerini sonuçta elde edilen derlenmiş koda katıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="a4da1-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="a4da1-119">COM türü, CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a4da1-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="a4da1-120">Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="a4da1-121">Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="a4da1-122">Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız hedef bilgisayarda .NET Framework 4 veya sonraki bir sürüm yüklendiği sürece başvurulan COM türlerini kullanabilir ve uygulamanız Yöntemler, özellikler veya uygulamalar kullanır. başvurulan COM türlerine dahil edilen olaylar.</span><span class="sxs-lookup"><span data-stu-id="a4da1-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="a4da1-123">`-link` Seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır.</span><span class="sxs-lookup"><span data-stu-id="a4da1-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="a4da1-124">COM sınıfları ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="a4da1-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4da1-125">Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="a4da1-126">CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4da1-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="a4da1-127">Visual Studio 'da `-link` seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4da1-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="a4da1-128">`Embed Interop Types` Özelliği için varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="a4da1-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="a4da1-129">Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a4da1-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="a4da1-130">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="a4da1-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="a4da1-131">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a4da1-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="a4da1-132">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4da1-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="a4da1-133">[/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4da1-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="a4da1-134">Derleyicinin Vbc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4da1-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="a4da1-135">`-link` Öğesinin`-l`kısa biçimi.</span><span class="sxs-lookup"><span data-stu-id="a4da1-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="a4da1-136">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="a4da1-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="a4da1-137">Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a4da1-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="a4da1-138">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a4da1-138">Generic Interfaces</span></span>  
 <span data-ttu-id="a4da1-139">Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a4da1-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="a4da1-140">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="a4da1-141">Genel parametrelere sahip türler</span><span class="sxs-lookup"><span data-stu-id="a4da1-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="a4da1-142">Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a4da1-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="a4da1-143">Bu kısıtlama, arabirimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="a4da1-144">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> <xref:Microsoft.Office.Interop.Excel> derlemede tanımlanan arabirimi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a4da1-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="a4da1-145">Bir kitaplık, <xref:Microsoft.Office.Interop.Excel> birlikte çalışma türlerini derlemeden katıştırır ve türü <xref:Microsoft.Office.Interop.Excel.Range> arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar, bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="a4da1-146">Aşağıdaki örnekte, istemci kodu hata olmadan <xref:System.Collections.IList> genel arabirimi döndüren yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="a4da1-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="a4da1-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4da1-147">Example</span></span>  
 <span data-ttu-id="a4da1-148">`OfficeApp.vb` Aşağıdaki komut satırı, `COMData1.dll` ve `COMData2.dll` için `OfficeApp.exe`kaynak dosya ve başvuru derlemelerini derler.</span><span class="sxs-lookup"><span data-stu-id="a4da1-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4da1-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4da1-149">See also</span></span>

- [<span data-ttu-id="a4da1-150">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a4da1-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a4da1-151">İzlenecek yol: Yönetilen derlemelerden tür ekleme</span><span class="sxs-lookup"><span data-stu-id="a4da1-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="a4da1-152">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4da1-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="a4da1-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="a4da1-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="a4da1-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="a4da1-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [<span data-ttu-id="a4da1-155">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a4da1-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a4da1-156">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="a4da1-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
