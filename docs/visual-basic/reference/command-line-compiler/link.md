---
description: Daha fazla bilgi edinin:-link (Visual Basic)
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
ms.openlocfilehash: 31d98d2c0fb0cbd8e8baff82869501a7ff0ea270
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475142"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="4b79a-103">-bağlantı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b79a-103">-link (Visual Basic)</span></span>

<span data-ttu-id="4b79a-104">Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="4b79a-104">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b79a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b79a-105">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="4b79a-106">veya</span><span class="sxs-lookup"><span data-stu-id="4b79a-106">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b79a-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="4b79a-107">Arguments</span></span>  
  
|<span data-ttu-id="4b79a-108">Terim</span><span class="sxs-lookup"><span data-stu-id="4b79a-108">Term</span></span>|<span data-ttu-id="4b79a-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="4b79a-109">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="4b79a-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-110">Required.</span></span> <span data-ttu-id="4b79a-111">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="4b79a-111">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="4b79a-112">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="4b79a-112">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b79a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b79a-113">Remarks</span></span>  

 <span data-ttu-id="4b79a-114">`-link`Seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b79a-114">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="4b79a-115">Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-115">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="4b79a-116">Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-116">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="4b79a-117">Bir örnek için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4b79a-117">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="4b79a-118">Seçeneğinin kullanılması `-link` özellıkle com birlikte çalışabilirliğine çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4b79a-118">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="4b79a-119">Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b79a-119">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="4b79a-120">`-link`Seçeneği, derleyicinin başvurulan birlikte çalışma DERLEMESINDEKI com tür bilgilerini sonuçta elde edilen derlenmiş koda katıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="4b79a-120">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="4b79a-121">COM türü, CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4b79a-121">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="4b79a-122">Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-122">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="4b79a-123">Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-123">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="4b79a-124">Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız başvurulan COM türlerini, .NET Framework 4 veya üzeri hedef bilgisayara yüklendiği sürece ve uygulamanız başvurulan COM türlerine dahil olan yöntemleri, özellikleri veya olayları kullandığında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b79a-124">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="4b79a-125">`-link`Seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır.</span><span class="sxs-lookup"><span data-stu-id="4b79a-125">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="4b79a-126">COM sınıfları ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4b79a-126">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b79a-127">Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-127">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="4b79a-128">CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="4b79a-128">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="4b79a-129">`-link`Visual Studio 'da seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliği **true** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4b79a-129">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="4b79a-130">Özelliği için varsayılan değer `Embed Interop Types` **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="4b79a-130">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="4b79a-131">Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="4b79a-131">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="4b79a-132">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="4b79a-132">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="4b79a-133">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b79a-133">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="4b79a-134">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b79a-134">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="4b79a-135">[-Reference](reference.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b79a-135">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="4b79a-136">Derleyicinin Vbc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](noconfig.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b79a-136">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="4b79a-137">Öğesinin kısa biçimi `-link` `-l` .</span><span class="sxs-lookup"><span data-stu-id="4b79a-137">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="4b79a-138">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="4b79a-138">Generics and Embedded Types</span></span>  

 <span data-ttu-id="4b79a-139">Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4b79a-139">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="4b79a-140">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="4b79a-140">Generic Interfaces</span></span>  

 <span data-ttu-id="4b79a-141">Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b79a-141">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="4b79a-142">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-142">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="4b79a-143">Genel parametrelere sahip türler</span><span class="sxs-lookup"><span data-stu-id="4b79a-143">Types That Have Generic Parameters</span></span>  

 <span data-ttu-id="4b79a-144">Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b79a-144">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="4b79a-145">Bu kısıtlama, arabirimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-145">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="4b79a-146">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> derlemede tanımlanan arabirimi göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel> .</span><span class="sxs-lookup"><span data-stu-id="4b79a-146">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="4b79a-147">Bir kitaplık, birlikte çalışma türlerini derlemeden katıştırır <xref:Microsoft.Office.Interop.Excel> ve türü arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar <xref:Microsoft.Office.Interop.Excel.Range> , bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-147">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="4b79a-148">Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> hata olmadan genel arabirimi döndüren yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="4b79a-148">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="4b79a-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b79a-149">Example</span></span>  

 <span data-ttu-id="4b79a-150">Aşağıdaki komut satırı, `OfficeApp.vb` ve için kaynak dosya ve başvuru derlemelerini `COMData1.dll` derler `COMData2.dll` `OfficeApp.exe` .</span><span class="sxs-lookup"><span data-stu-id="4b79a-150">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b79a-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b79a-151">See also</span></span>

- [<span data-ttu-id="4b79a-152">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="4b79a-152">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4b79a-153">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="4b79a-153">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="4b79a-154">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b79a-154">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="4b79a-155">-noconfig</span><span class="sxs-lookup"><span data-stu-id="4b79a-155">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="4b79a-156">-libpath</span><span class="sxs-lookup"><span data-stu-id="4b79a-156">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="4b79a-157">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="4b79a-157">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4b79a-158">COM Birlikte Çalışma'ya Giriş</span><span class="sxs-lookup"><span data-stu-id="4b79a-158">Introduction to COM Interop</span></span>](../../programming-guide/com-interop/introduction-to-com-interop.md)
