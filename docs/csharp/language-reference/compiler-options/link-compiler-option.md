---
title: -Link (C# derleyici seçenekleri)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 724a848d4c31b2c4f6fc3427d70fc84f4fd944c6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924757"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="6d80f-102">-Link (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6d80f-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="6d80f-103">Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6d80f-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d80f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d80f-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d80f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6d80f-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="6d80f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6d80f-106">Required.</span></span> <span data-ttu-id="6d80f-107">Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="6d80f-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="6d80f-108">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="6d80f-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d80f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d80f-109">Remarks</span></span>  
 <span data-ttu-id="6d80f-110">`-link` Seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d80f-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="6d80f-111">Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="6d80f-112">Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="6d80f-113">Bir örnek için bkz [. İzlenecek yol: Yönetilen derlemelerden](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)türler ekleme.</span><span class="sxs-lookup"><span data-stu-id="6d80f-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="6d80f-114">`-link` Seçeneğinin kullanılması özellikle com birlikte çalışabilirliğine çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6d80f-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="6d80f-115">Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d80f-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="6d80f-116">`-link` Seçeneği, derleyicinin başvurulan birlikte çalışma derlemesindeki com tür bilgilerini sonuçta elde edilen derlenmiş koda katıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="6d80f-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="6d80f-117">COM türü, CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6d80f-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="6d80f-118">Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="6d80f-119">Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="6d80f-120">Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız hedef bilgisayarda .NET Framework 4 veya sonraki bir sürüm yüklendiği sürece başvurulan COM türlerini kullanabilir ve uygulamanız Yöntemler, özellikler veya uygulamalar kullanır. başvurulan COM türlerine dahil edilen olaylar.</span><span class="sxs-lookup"><span data-stu-id="6d80f-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="6d80f-121">`-link` Seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır.</span><span class="sxs-lookup"><span data-stu-id="6d80f-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="6d80f-122">COM sınıfları ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="6d80f-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d80f-123">Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="6d80f-124">CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="6d80f-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="6d80f-125">Visual Studio 'da `-link` seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d80f-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="6d80f-126">`Embed Interop Types` Özelliği için varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="6d80f-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="6d80f-127">Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d80f-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="6d80f-128">Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="6d80f-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="6d80f-129">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6d80f-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="6d80f-130">[-Reference](./reference-compiler-option.md) derleyici seçeneği gibi, `-link` derleyici seçeneği sık kullanılan .NET Framework derlemelerine başvuran Csc. rsp yanıt dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d80f-130">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="6d80f-131">Derleyicinin Csc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d80f-131">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="6d80f-132">`-link` Öğesinin`-l`kısa biçimi.</span><span class="sxs-lookup"><span data-stu-id="6d80f-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="6d80f-133">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="6d80f-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="6d80f-134">Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6d80f-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="6d80f-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6d80f-135">Generic Interfaces</span></span>  
 <span data-ttu-id="6d80f-136">Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d80f-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="6d80f-137">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="6d80f-138">Genel parametrelere sahip türler</span><span class="sxs-lookup"><span data-stu-id="6d80f-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="6d80f-139">Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6d80f-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="6d80f-140">Bu kısıtlama, arabirimler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="6d80f-141">Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> <xref:Microsoft.Office.Interop.Excel> derlemede tanımlanan arabirimi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6d80f-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="6d80f-142">Bir kitaplık, <xref:Microsoft.Office.Interop.Excel> birlikte çalışma türlerini derlemeden katıştırır ve türü <xref:Microsoft.Office.Interop.Excel.Range> arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar, bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="6d80f-143">Aşağıdaki örnekte, istemci kodu hata olmadan <xref:System.Collections.IList> genel arabirimi döndüren yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="6d80f-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="6d80f-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d80f-144">Example</span></span>  
 <span data-ttu-id="6d80f-145">Aşağıdaki `OfficeApp.cs` kod, `COMData1.dll` ve `COMData2.dll` için kaynakdosyasıvebaşvuruderlemeleriniderler.`OfficeApp.exe`</span><span class="sxs-lookup"><span data-stu-id="6d80f-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d80f-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d80f-146">See also</span></span>

- [<span data-ttu-id="6d80f-147">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6d80f-147">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6d80f-148">İzlenecek yol: Yönetilen derlemelerden tür ekleme</span><span class="sxs-lookup"><span data-stu-id="6d80f-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="6d80f-149">-Reference (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6d80f-149">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="6d80f-150">-noconfig (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6d80f-150">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="6d80f-151">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="6d80f-151">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="6d80f-152">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6d80f-152">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
