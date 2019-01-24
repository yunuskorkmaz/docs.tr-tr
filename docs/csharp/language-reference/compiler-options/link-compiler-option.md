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
ms.openlocfilehash: 08b09a762a62e758c1c396b80b46648725b835b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500570"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="e9931-102">-bağlantı (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e9931-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="e9931-103">Derleyici COM tür bilgilerini belirli derlemelerde şu anda derleme proje kullanılabilir hale getirmek neden olur.</span><span class="sxs-lookup"><span data-stu-id="e9931-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9931-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9931-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9931-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9931-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="e9931-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e9931-106">Required.</span></span> <span data-ttu-id="e9931-107">Derleme dosya adlarının virgülle ayrılmış liste.</span><span class="sxs-lookup"><span data-stu-id="e9931-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="e9931-108">Dosya adı boşluk içeriyorsa adı tırnak içine alın.</span><span class="sxs-lookup"><span data-stu-id="e9931-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9931-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9931-109">Remarks</span></span>  
 <span data-ttu-id="e9931-110">`-link` Seçeneği, gömülü tür bilgileri içeren bir uygulama dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9931-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="e9931-111">Uygulama, daha sonra bir çalışma zamanı derlemesindeki gömülü tür bilgileri, çalışma zamanı derlemeye bir başvuruda gerek kalmadan uygulayan türler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9931-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="e9931-112">Çeşitli çalışma zamanı derleme sürümleri yayımladıysanız, gömülü tür bilgileri içeren uygulama derlenmesi gerek kalmadan çeşitli sürümleriyle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="e9931-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="e9931-113">Bir örnek için bkz [izlenecek yol: Yönetilen derlemeler türler katıştırma](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="e9931-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="e9931-114">Kullanarak `-link` COM birlikte çalışma ile çalışırken seçenek özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9931-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="e9931-115">Uygulamanız artık hedef bilgisayarda birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e9931-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="e9931-116">`-link` Başvurulan birlikte çalışma bütünleştirilmiş kod içine ortaya çıkan derlenmiş kodu COM tür bilgilerini katıştırma derleyici seçeneği bildirir.</span><span class="sxs-lookup"><span data-stu-id="e9931-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="e9931-117">COM türü (GUID) CLSID değeri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e9931-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="e9931-118">Sonuç olarak, uygulamanızı aynı COM türlerini aynı CLSID değerlerle yüklü olduğu bir hedef bilgisayarda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9931-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="e9931-119">Microsoft Office otomatikleştirmek uygulamaların iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e9931-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="e9931-120">Office gibi uygulamalarda, genellikle aynı CLSID değeri farklı sürümler arasında tutmak olduğundan, uygulamanızı başvurulan COM türlerini uzun olarak .NET Framework 4 veya daha sonra hedef bilgisayarda yüklü olduğundan ve yöntemler, özellikler, uygulamanızın kullandığı gibi kullanabilirsiniz veya Başvurulan COM türlerini dahil edilen olaylar.</span><span class="sxs-lookup"><span data-stu-id="e9931-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="e9931-121">`-link` Seçeneği yalnızca arabirimleri, yapılar ve temsilciler ekler.</span><span class="sxs-lookup"><span data-stu-id="e9931-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="e9931-122">COM sınıfları ekleme desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e9931-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9931-123">Kodunuzda katıştırılmış bir COM türün örneğini oluşturduğunuzda, uygun arabirimini kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9931-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="e9931-124">Coclass'ı kullanarak katıştırılmış bir COM tür örneği oluşturulmaya çalışılırken bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="e9931-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="e9931-125">Ayarlanacak `-link` seçeneğini Visual Studio'da ve bir bütünleştirilmiş kod Başvurusu Ekle `Embed Interop Types` özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="e9931-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="e9931-126">İçin varsayılan `Embed Interop Types` özelliği **false**.</span><span class="sxs-lookup"><span data-stu-id="e9931-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="e9931-127">Bir COM derlemesine (bütünleştirilmiş kod: A) bağlarsanız kendisi başka bir COM derlemesine (derleme B) başvuruda, aşağıdakilerden biri doğruysa, derleme B bağlamak de:</span><span class="sxs-lookup"><span data-stu-id="e9931-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="e9931-128">Bir derlemeden bir tür bir tür tarafından devralındığında veya derleme B'deki bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="e9931-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="e9931-129">Bir alan, özelliği, olay veya dönüş türü veya parametresi türü derleme b olan yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e9931-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="e9931-130">Gibi [-başvuru](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği `-link` derleyici seçeneği başvuru sık kullanılan Csc.rsp yanıt dosyası kullanan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler.</span><span class="sxs-lookup"><span data-stu-id="e9931-130">Like the [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="e9931-131">Kullanma [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Csc.rsp dosyasını kullanmak için derleyicinin istemiyorsanız derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e9931-131">Use the [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="e9931-132">Kısa formunu da `-link` olduğu `-l`.</span><span class="sxs-lookup"><span data-stu-id="e9931-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="e9931-133">Genel türler ve gömülü türleri</span><span class="sxs-lookup"><span data-stu-id="e9931-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="e9931-134">Aşağıdaki bölümlerde, genel türleri kullanarak birlikte çalışma türlerini katıştır uygulamalarda sınırlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9931-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="e9931-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e9931-135">Generic Interfaces</span></span>  
 <span data-ttu-id="e9931-136">Gömülü birlikte çalışma derlemesi genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9931-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="e9931-137">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e9931-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="e9931-138">Genel parametre türleri</span><span class="sxs-lookup"><span data-stu-id="e9931-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="e9931-139">Genel parametre türü bir birlikte çalışma derlemesi katıştırılmış türleri, dış bütünleştirilmiş koddan tür olan kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9931-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="e9931-140">Bu kısıtlama, arabirimler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e9931-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="e9931-141">Örneğin, düşünün <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi <xref:Microsoft.Office.Interop.Excel> derleme.</span><span class="sxs-lookup"><span data-stu-id="e9931-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="e9931-142">Birlikte çalışma türleri bir kitaplığını katıştırır, <xref:Microsoft.Office.Interop.Excel> bütünleştirilmiş kod ve türü olan bir parametreye sahip genel bir tür döndüren bir yöntem sunarsa <xref:Microsoft.Office.Interop.Excel.Range> arabirim yöntemi aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9931-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 <span data-ttu-id="e9931-143">Aşağıdaki örnekte, istemci kodu döndüren yöntem çağırabilirsiniz <xref:System.Collections.IList> hatasız genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="e9931-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="e9931-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9931-144">Example</span></span>  
 <span data-ttu-id="e9931-145">Aşağıdaki kod, kaynak dosyasını derler `OfficeApp.cs` ve başvuru derlemeleri `COMData1.dll` ve `COMData2.dll` üretmek için `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="e9931-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9931-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9931-146">See also</span></span>

- [<span data-ttu-id="e9931-147">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e9931-147">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="e9931-148">İzlenecek yol: Yönetilen derlemelerden türler katıştırma</span><span class="sxs-lookup"><span data-stu-id="e9931-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="e9931-149">-başvurusu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e9931-149">-reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
- [<span data-ttu-id="e9931-150">-noconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e9931-150">-noconfig (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)
- [<span data-ttu-id="e9931-151">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="e9931-151">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e9931-152">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9931-152">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
