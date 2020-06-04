---
title: -link
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
ms.openlocfilehash: 6082806591d398aa8b16b44e769a3f8078ce62d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387744"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="bff17-102">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bff17-102">-link (Visual Basic)</span></span>
<span data-ttu-id="bff17-103">Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="bff17-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bff17-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bff17-104">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="bff17-105">veya</span><span class="sxs-lookup"><span data-stu-id="bff17-105">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bff17-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="bff17-106">Arguments</span></span>  
  
|<span data-ttu-id="bff17-107">Terim</span><span class="sxs-lookup"><span data-stu-id="bff17-107">Term</span></span>|<span data-ttu-id="bff17-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="bff17-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="bff17-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bff17-109">Required.</span></span> <span data-ttu-id="bff17-110">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="bff17-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="bff17-111">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="bff17-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bff17-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bff17-112">Remarks</span></span>  
 <span data-ttu-id="bff17-113">`-link`Seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bff17-113">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="bff17-114">Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="bff17-114">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="bff17-115">Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="bff17-115">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="bff17-116">Bir örnek için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="bff17-116">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="bff17-117">Seçeneğinin kullanılması `-link` özellıkle com birlikte çalışabilirliğine çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bff17-117">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="bff17-118">Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bff17-118">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="bff17-119">`-link`Seçeneği, derleyicinin başvurulan birlikte çalışma DERLEMESINDEKI com tür bilgilerini sonuçta elde edilen derlenmiş koda katıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="bff17-119">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="bff17-120">COM türü, CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bff17-120">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="bff17-121">Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="bff17-121">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="bff17-122">Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="bff17-122">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="bff17-123">Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız başvurulan COM türlerini, .NET Framework 4 veya üzeri hedef bilgisayara yüklendiği sürece ve uygulamanız başvurulan COM türlerine dahil olan yöntemleri, özellikleri veya olayları kullandığında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bff17-123">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="bff17-124">`-link`Seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır.</span><span class="sxs-lookup"><span data-stu-id="bff17-124">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="bff17-125">COM sınıfları ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="bff17-125">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bff17-126">Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bff17-126">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="bff17-127">CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="bff17-127">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="bff17-128">`-link`Visual Studio 'da seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bff17-128">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="bff17-129">Özelliği için varsayılan değer `Embed Interop Types` **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="bff17-129">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="bff17-130">Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="bff17-130">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="bff17-131">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="bff17-131">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="bff17-132">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bff17-132">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="bff17-133">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bff17-133">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="bff17-134">[-Reference](reference.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="bff17-134">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="bff17-135">Derleyicinin Vbc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](noconfig.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bff17-135">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="bff17-136">Öğesinin kısa biçimi `-link` `-l` .</span><span class="sxs-lookup"><span data-stu-id="bff17-136">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="bff17-137">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="bff17-137">Generics and Embedded Types</span></span>  
 <span data-ttu-id="bff17-138">Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bff17-138">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="bff17-139">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bff17-139">Generic Interfaces</span></span>  
 <span data-ttu-id="bff17-140">Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bff17-140">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="bff17-141">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="bff17-141">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="bff17-142">Genel parametrelere sahip türler</span><span class="sxs-lookup"><span data-stu-id="bff17-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="bff17-143">Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bff17-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="bff17-144">Bu kısıtlama, arabirimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bff17-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="bff17-145">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> derlemede tanımlanan arabirimi göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel> .</span><span class="sxs-lookup"><span data-stu-id="bff17-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="bff17-146">Bir kitaplık, birlikte çalışma türlerini derlemeden katıştırır <xref:Microsoft.Office.Interop.Excel> ve türü arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar <xref:Microsoft.Office.Interop.Excel.Range> , bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="bff17-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="bff17-147">Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> hata olmadan genel arabirimi döndüren yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="bff17-147">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="bff17-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="bff17-148">Example</span></span>  
 <span data-ttu-id="bff17-149">Aşağıdaki komut satırı, `OfficeApp.vb` ve için kaynak dosya ve başvuru derlemelerini `COMData1.dll` derler `COMData2.dll` `OfficeApp.exe` .</span><span class="sxs-lookup"><span data-stu-id="bff17-149">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bff17-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bff17-150">See also</span></span>

- [<span data-ttu-id="bff17-151">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bff17-151">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bff17-152">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="bff17-152">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="bff17-153">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bff17-153">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="bff17-154">-noconfig</span><span class="sxs-lookup"><span data-stu-id="bff17-154">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="bff17-155">-libpath</span><span class="sxs-lookup"><span data-stu-id="bff17-155">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="bff17-156">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="bff17-156">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="bff17-157">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="bff17-157">Introduction to COM Interop</span></span>](../../programming-guide/com-interop/introduction-to-com-interop.md)
