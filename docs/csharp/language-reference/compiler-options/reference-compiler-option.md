---
title: -başvurusu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 131cdf62917ab2fc8d564b85c30d13c8971e5809
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361884"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="29c40-102">-başvurusu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="29c40-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="29c40-103">**-Başvuru** içeri aktarmak derleyici seçeneği neden [genel](../../../csharp/language-reference/keywords/public.md) tür bilgilerini belirtilen dosyada geçerli projeye bu nedenle belirtilen derleme dosyalarından meta verileri başvuru etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="29c40-103">The **-reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29c40-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="29c40-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="29c40-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="29c40-106">Bir derleme bildirimi içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="29c40-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="29c40-107">Birden fazla dosya aktarmak için ayrı bir dahil **-başvuru** seçeneği her dosya için.</span><span class="sxs-lookup"><span data-stu-id="29c40-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="29c40-108">Derlemedeki tüm ad alanlarını içerecek bir kök ad alanını temsil eden geçerli bir C# tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="29c40-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29c40-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29c40-109">Remarks</span></span>  
 <span data-ttu-id="29c40-110">Birden fazla dosyadan, eklenecek bir **-başvuru** seçeneği her dosya için.</span><span class="sxs-lookup"><span data-stu-id="29c40-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="29c40-111">İçeri aktardığınız dosya, bir bildirim içermesi gerekir; Çıkış dosyası biri ile derlenmiş olmalıdır [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="29c40-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="29c40-112">**-r** öğesinin kısa biçimidir **-başvuru**.</span><span class="sxs-lookup"><span data-stu-id="29c40-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="29c40-113">Kullanım [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) meta verileri, bir derleme bildirimi içermeyen bir çıkış dosyasından içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="29c40-113">Use [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="29c40-114">(Derleme B) başka bir derlemeye başvuran bir derlemeye (a derlemesi) başvuruda bulunursanız, derleme B başvuru gerekir:</span><span class="sxs-lookup"><span data-stu-id="29c40-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="29c40-115">Kullandığınız bir derlemeden bir tür bir tür tarafından devralındığında veya derleme B'deki bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="29c40-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="29c40-116">Bir alan, özelliği, olay veya bir dönüş türü veya parametre türü derleme B'deki yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="29c40-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="29c40-117">Kullanım [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) için bir veya daha fazla, derleme başvuruları bulunduğu dizini belirtin.</span><span class="sxs-lookup"><span data-stu-id="29c40-117">Use [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="29c40-118">**-Lib** konu ayrıca derleyicinin derlemeler için arama dizinleri anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29c40-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="29c40-119">Derleyicinin derlemede ve bir modüldeki bir türü tanıması için bu türün bir örneğini tanımlayarak yapabilirsiniz türü çözümlemeye zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29c40-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="29c40-120">Derleyici bir derlemede bulunan tür adlarını çözmek için farklı yöntemleri vardır: bir derleme içinde bulunan bir türden devralıyorsanız, örneğin, tür adı ardından derleyici tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="29c40-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="29c40-121">Bazen bir derlemenin içinde aynı bileşenin farklı iki versiyonunu başvurmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="29c40-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="29c40-122">Bunu yapmak için üzerinde üstündeki takma alt seçeneği kullanmak **-başvuru** geçiş iki dosya arasında ayrım yapmak her bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="29c40-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="29c40-123">Bu diğer adı, bileşen adı için bir niteleyici kullanılacak ve bileşen dosyalarından birini çözülecektir.</span><span class="sxs-lookup"><span data-stu-id="29c40-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="29c40-124">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran, csc yanıt (.rsp) dosyasını, varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29c40-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="29c40-125">Kullanma [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) derleyici csc.rsp kullanmak istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="29c40-125">Use [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29c40-126">Visual Studio'da kullanmak **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="29c40-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="29c40-127">Daha fazla bilgi için [nasıl yapılır: başvurular ekleme veya kaldırma başvuru Yöneticisi'ni kullanarak](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="29c40-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="29c40-128">Kullanarak başvurular ekleme arasında eşdeğer davranışı sağlamak açısından `-reference` ve kullanarak başvurular ekleme **Başvuru Ekle** iletişim kutusu, kümesi **birlikte çalışma türlerini katıştır** özelliğini**False** eklemekte derleme.</span><span class="sxs-lookup"><span data-stu-id="29c40-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="29c40-129">**Doğru** özelliği için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="29c40-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c40-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="29c40-130">Example</span></span>  
 <span data-ttu-id="29c40-131">Bu örnek nasıl kullanılacağını gösterir [extern diğer adı](../../../csharp/language-reference/keywords/extern-alias.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="29c40-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="29c40-132">Kaynak dosyasını derlemek ve meta verileri alma `grid.dll` ve `grid20.dll`, hangi önceden derlenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="29c40-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="29c40-133">Aynı bileşenin farklı sürümleri iki DLL içeren ve iki kullandığınız **-başvuru** kaynak dosyasını derlemek için diğer seçeneklere sahip.</span><span class="sxs-lookup"><span data-stu-id="29c40-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="29c40-134">Seçenekler şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="29c40-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="29c40-135">Bu dış isimlerini ayarlar `GridV1` ve `GridV2`, programınızdaki yoluyla kullanan bir `extern` deyimi:</span><span class="sxs-lookup"><span data-stu-id="29c40-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="29c40-136">Bunu yaptıktan sonra kılavuz denetiminden başvurabilirsiniz `grid.dll` denetim adını tarafından `GridV1`, şöyle:</span><span class="sxs-lookup"><span data-stu-id="29c40-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="29c40-137">Ayrıca, kılavuz denetiminden başvurabilirsiniz `grid20.dll` denetim adını tarafından `GridV2` şöyle:</span><span class="sxs-lookup"><span data-stu-id="29c40-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="29c40-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29c40-138">See Also</span></span>  

- [<span data-ttu-id="29c40-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="29c40-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="29c40-140">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="29c40-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
