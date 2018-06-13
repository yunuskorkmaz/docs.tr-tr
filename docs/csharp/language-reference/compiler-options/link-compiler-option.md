---
title: -bağlantı (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 668476beb2eefa7a818f60606443ae06ae26a17d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217213"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="9f075-102">-bağlantı (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9f075-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="9f075-103">Derleyici COM türü bilgileri belirtilen derlemelerde şu anda derlediğiniz proje kullanılabilir hale getirmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="9f075-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f075-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f075-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f075-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f075-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="9f075-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9f075-106">Required.</span></span> <span data-ttu-id="9f075-107">Derleme dosya adlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="9f075-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="9f075-108">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="9f075-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f075-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f075-109">Remarks</span></span>  
 <span data-ttu-id="9f075-110">`-link` Seçeneği katıştırılmış türde bilgi içeren bir uygulama dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f075-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="9f075-111">Uygulamanın gömülü tür bilgileri çalışma zamanı derlemesine başvuru gerek kalmadan uygulama çalışma zamanı derlemesi türlerinde sonra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f075-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="9f075-112">Çeşitli çalışma zamanı derleme sürümleri yayımladıysanız katıştırılmış tür bilgileri içeren uygulama derlenmesi gerek kalmadan çeşitli sürümleriyle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="9f075-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="9f075-113">Bir örnek için bkz: [izlenecek yol: yönetilen derlemelerden türler katıştırma](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9f075-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="9f075-114">Kullanarak `-link` COM birlikte çalışma ile çalışırken seçenek özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9f075-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="9f075-115">Böylelikle, uygulamanızın artık hedef bilgisayarda birincil birlikte çalışma derlemesi (PIA) gerektirir COM türlerini eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9f075-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="9f075-116">`-link` Seçeneği elde edilen derlenmiş kod başvurulan birlikte çalışma derlemeye COM tür bilgilerini katıştırma derleyici bildirir.</span><span class="sxs-lookup"><span data-stu-id="9f075-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="9f075-117">COM türü CLSID (GUID) değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9f075-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="9f075-118">Sonuç olarak, uygulamanızı aynı CLSID değerlerine sahip aynı COM türlerini yüklü olduğu bir hedef bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f075-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="9f075-119">Microsoft Office'i otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="9f075-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="9f075-120">Office gibi uygulamalar genellikle farklı sürümleri arasında aynı CLSID değeri tutmak için uygulamanız başvurulan COM türlerini uzun .NET Framework 4 veya daha sonra hedef bilgisayarda yüklü olduğundan ve yöntemler, özellikler, uygulamanızın kullandığı gibi kullanabilirsiniz veya Başvurulan COM türlerinde dahil olaylar.</span><span class="sxs-lookup"><span data-stu-id="9f075-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="9f075-121">`-link` Seçeneği yalnızca arabirimleri, yapılar ve temsilciler katıştırır.</span><span class="sxs-lookup"><span data-stu-id="9f075-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="9f075-122">COM sınıfları katıştırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9f075-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f075-123">Kodunuzda katıştırılmış COM türünün bir örneğini oluştururken uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f075-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="9f075-124">Coclass'ı kullanarak katıştırılmış COM türünün bir örneği oluşturulmaya çalışılırken bir hata neden olur.</span><span class="sxs-lookup"><span data-stu-id="9f075-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="9f075-125">Ayarlamak için `-link` seçeneği Visual Studio'da ve bir derleme başvurusu Ekle `Embed Interop Types` özelliğine **doğru**.</span><span class="sxs-lookup"><span data-stu-id="9f075-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="9f075-126">İçin varsayılan `Embed Interop Types` özelliği **false**.</span><span class="sxs-lookup"><span data-stu-id="9f075-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="9f075-127">Bir COM derlemesine (a derlemesi) bağlantısının kendisi başka bir COM derlemesine (derleme B) başvuruyor, aşağıdakilerden biri doğruysa B derlemesine bağlantı gerekir:</span><span class="sxs-lookup"><span data-stu-id="9f075-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="9f075-128">Derlemesi türünden bir türden devralır veya derleme B'deki bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="9f075-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="9f075-129">Alan, özellik, olay veya b derlemesinden dönüş türü veya parametresi türü olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9f075-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="9f075-130">Gibi [-başvuru](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği `-link` derleyici seçeneği başvuruları sık kullanılan Csc.rsp yanıt dosyası kullanan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler.</span><span class="sxs-lookup"><span data-stu-id="9f075-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="9f075-131">Kullanmak [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) derleyicinin Csc.rsp dosyasını kullanmasını istemiyorsanız derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9f075-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="9f075-132">Kısa formunu `-link` olan `-l`.</span><span class="sxs-lookup"><span data-stu-id="9f075-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="9f075-133">Genel türler ve katıştırılmış türler</span><span class="sxs-lookup"><span data-stu-id="9f075-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="9f075-134">Aşağıdaki bölümlerde, genel türler birlikte çalışma türlerini katıştır uygulamalarında kullanma sınırlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f075-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="9f075-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="9f075-135">Generic Interfaces</span></span>  
 <span data-ttu-id="9f075-136">Birlikte çalışma bir derlemeden katıştırılmış genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f075-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="9f075-137">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9f075-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="9f075-138">Genel Parametreler türleri</span><span class="sxs-lookup"><span data-stu-id="9f075-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="9f075-139">Türü birlikte çalışma bir derlemeden katıştırılmış genel bir parametre türleri, dış bir derlemeden tür olan kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f075-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="9f075-140">Bu kısıtlama, arabirimler için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9f075-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="9f075-141">Örneğin, göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi <xref:Microsoft.Office.Interop.Excel> derleme.</span><span class="sxs-lookup"><span data-stu-id="9f075-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="9f075-142">Birlikte çalışma türlerini kitaplık katıştırır, <xref:Microsoft.Office.Interop.Excel> derleme ve bir parametreye sahip genel bir tür, türü döndüren bir yöntem sunarsa <xref:Microsoft.Office.Interop.Excel.Range> arabirim, yöntem aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="9f075-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 <span data-ttu-id="9f075-143">Aşağıdaki örnekte, istemci kodu döndürür yöntemini çağırabilir <xref:System.Collections.IList> hatasız genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="9f075-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="9f075-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f075-144">Example</span></span>  
 <span data-ttu-id="9f075-145">Aşağıdaki kod kaynak dosyasını derler `OfficeApp.cs` ve başvuru derlemelerden `COMData1.dll` ve `COMData2.dll` üretmek için `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="9f075-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f075-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f075-146">See Also</span></span>  
 [<span data-ttu-id="9f075-147">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9f075-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="9f075-148">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="9f075-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="9f075-149">-reference (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9f075-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [<span data-ttu-id="9f075-150">-noconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="9f075-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [<span data-ttu-id="9f075-151">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="9f075-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="9f075-152">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9f075-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
