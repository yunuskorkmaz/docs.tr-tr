---
title: -link (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 4c96f7be5ac500886ea036c93b4651fa814ee58a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970104"
---
# <a name="-link-c-compiler-options"></a><span data-ttu-id="c93df-102">-link (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c93df-102">-link (C# Compiler Options)</span></span>
<span data-ttu-id="c93df-103">Derleyicinin, şu anda derlemekte olduğunuz projeiçin belirtilen derlemelerde COM türü bilgilerini kullanılabilir hale getirmelerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c93df-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c93df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c93df-104">Syntax</span></span>  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="c93df-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c93df-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="c93df-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c93df-106">Required.</span></span> <span data-ttu-id="c93df-107">Derleme dosya adlarının virgülle sınırlandırıladaki listesi.</span><span class="sxs-lookup"><span data-stu-id="c93df-107">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="c93df-108">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretlerine ekin.</span><span class="sxs-lookup"><span data-stu-id="c93df-108">If the file name contains a space, enclose the name in quotation marks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c93df-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c93df-109">Remarks</span></span>  
 <span data-ttu-id="c93df-110">Bu `-link` seçenek, tür bilgilerini katıştüre eden bir uygulama dağıtmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c93df-110">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="c93df-111">Uygulama daha sonra, çalışma zamanı derlemesine başvuru gerektirmeden katıştırılmış tür bilgilerini uygulayan çalışma zamanı derlemesi türlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c93df-111">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="c93df-112">Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanırsa, katıştılı tür bilgilerini içeren uygulama yeniden derlenmek zorunda kalmadan çeşitli sürümlerle çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c93df-112">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="c93df-113">Örneğin, [Bkz. Walkthrough: Yönetilen Derlemelerden Türleri Katıştırma.](../../../standard/assembly/embed-types-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="c93df-113">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="c93df-114">`-link` Seçeneği kullanmak özellikle COM interop ile çalışırken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c93df-114">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="c93df-115">Com türlerini, uygulamanızın artık hedef bilgisayara birincil interop derlemesi (PIA) gerektirmeyin diye katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c93df-115">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="c93df-116">Seçenek, `-link` derleyiciye, başvurulan interop derlemesinden COM türü bilgilerini elde edilen derlenmiş koda gömmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c93df-116">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="c93df-117">COM türü CLSID (GUID) değeri ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c93df-117">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="c93df-118">Sonuç olarak, uygulamanız aynı CLSID değerlerine sahip aynı COM türlerini yüklemiş bir hedef bilgisayarda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c93df-118">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="c93df-119">Microsoft Office'i otomatikleştiren uygulamalar iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="c93df-119">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="c93df-120">Office gibi uygulamalar genellikle farklı sürümler arasında aynı CLSID değerini tuttuğundan, başvurulan COM türlerini hedef bilgisayara .NET Framework 4 veya sonraki olarak yüklenmiş ve uygulamanız yöntemleri, özellikleri veya başvurulan COM türlerine dahil olan olaylar.</span><span class="sxs-lookup"><span data-stu-id="c93df-120">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="c93df-121">Seçenek `-link` yalnızca arabirimleri, yapıları ve temsilcileri katıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="c93df-121">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="c93df-122">Gömme COM sınıfları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c93df-122">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c93df-123">Kodunuzda gömülü bir COM türü örneği oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c93df-123">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="c93df-124">CoClass kullanarak katıştırılmış com türü bir örnek oluşturmaya çalışırken bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c93df-124">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="c93df-125">Visual Studio'da `-link` seçeneği ayarlamak için bir montaj `Embed Interop Types` başvurusu ekleyin ve özelliği **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c93df-125">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="c93df-126">`Embed Interop Types` Özellik için varsayılan **yanlıştır.**</span><span class="sxs-lookup"><span data-stu-id="c93df-126">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="c93df-127">Başka bir COM derlemesine (B Derlemesi) atıfta bulunan bir COM derlemesine (A Derlemesi) bağlantı verirseniz, aşağıdakilerden biri doğruysa B Derlemesi'ne de bağlanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c93df-127">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="c93df-128">A Derlemesi'nden bir tür bir türdevralır veya B Derlemesi'nden bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="c93df-128">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="c93df-129">B derlemesinden iade türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c93df-129">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="c93df-130">[-başvuru](./reference-compiler-option.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık sık kullanılan .NET Framework derlemelerine başvuran Csc.rsp yanıt dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c93df-130">Like the [-reference](./reference-compiler-option.md) compiler option, the `-link` compiler option uses the Csc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="c93df-131">Derleyicinin Csc.rsp dosyasını kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c93df-131">Use the [-noconfig](./noconfig-compiler-option.md) compiler option if you do not want the compiler to use the Csc.rsp file.</span></span>  
  
 <span data-ttu-id="c93df-132">Kısa formu `-link` `-l`.</span><span class="sxs-lookup"><span data-stu-id="c93df-132">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="c93df-133">Genel ler ve Gömülü Türler</span><span class="sxs-lookup"><span data-stu-id="c93df-133">Generics and Embedded Types</span></span>  
 <span data-ttu-id="c93df-134">Aşağıdaki bölümlerde interop türleri katıştırma uygulamalarında genel türleri kullanarak sınırlamaları açıklayınız.</span><span class="sxs-lookup"><span data-stu-id="c93df-134">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="c93df-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="c93df-135">Generic Interfaces</span></span>  
 <span data-ttu-id="c93df-136">Interop derlemesinden katıştürilmiş genel arabirimler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c93df-136">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="c93df-137">Bu, aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c93df-137">This is shown in the following example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="c93df-138">Genel Parametrelere Sahip Türler</span><span class="sxs-lookup"><span data-stu-id="c93df-138">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="c93df-139">Bu tür harici bir derlemeden geliyorsa, türü bir interop derlemesinden katıştırılmış genel bir parametreye sahip türler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c93df-139">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="c93df-140">Bu kısıtlama arabirimler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c93df-140">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="c93df-141">Örneğin, <xref:Microsoft.Office.Interop.Excel> derlemede <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c93df-141">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="c93df-142">Kitaplık derlemeden interop türlerini <xref:Microsoft.Office.Interop.Excel> katıştırır ve türü <xref:Microsoft.Office.Interop.Excel.Range> arabirim olan bir parametreye sahip genel bir türdöndüren bir yöntem ortaya çıkarırsa, bu yöntemin aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c93df-142">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 <span data-ttu-id="c93df-143">Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> genel arabirimi hatasız döndüren yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="c93df-143">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a><span data-ttu-id="c93df-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="c93df-144">Example</span></span>  
 <span data-ttu-id="c93df-145">Aşağıdaki kod kaynak dosya `OfficeApp.cs` ve başvuru `COMData1.dll` derlemeleri derler ve `COMData2.dll` üretmek `OfficeApp.exe`için.</span><span class="sxs-lookup"><span data-stu-id="c93df-145">The following code compiles source file `OfficeApp.cs` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c93df-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c93df-146">See also</span></span>

- [<span data-ttu-id="c93df-147">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c93df-147">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c93df-148">İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma</span><span class="sxs-lookup"><span data-stu-id="c93df-148">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="c93df-149">-referans (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c93df-149">-reference (C# Compiler Options)</span></span>](./reference-compiler-option.md)
- [<span data-ttu-id="c93df-150">-noconfig (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c93df-150">-noconfig (C# Compiler Options)</span></span>](./noconfig-compiler-option.md)
- [<span data-ttu-id="c93df-151">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="c93df-151">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
- [<span data-ttu-id="c93df-152">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c93df-152">Interoperability Overview</span></span>](../../programming-guide/interop/interoperability-overview.md)
