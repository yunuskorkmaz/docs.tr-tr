---
title: "-reference (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /reference
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
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b3995cd22f50aa8a3a329b22a4fbe4e9b8ffa4ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-c-compiler-options"></a><span data-ttu-id="1f5e0-102">/reference (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1f5e0-102">/reference (C# Compiler Options)</span></span>
<span data-ttu-id="1f5e0-103">**/Reference** seçeneği neden içeri aktarmak derleyici [ortak](../../../csharp/language-reference/keywords/public.md) tür bilgilerini belirtilen dosya geçerli projeye böylece belirtilen derleme dosyalarından meta verileri başvuru etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-103">The **/reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f5e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f5e0-104">Syntax</span></span>  
  
```console  
/reference:[alias=]filename  
/reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f5e0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f5e0-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="1f5e0-106">Bir derleme bildirimi içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="1f5e0-107">Birden fazla dosyayı içeri aktarmak için ayrı bir dahil **/reference** her dosya için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-107">To import more than one file, include a separate **/reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="1f5e0-108">Derlemedeki tüm ad alanlarını içerecek bir kök ad alanını temsil eden geçerli bir C# tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f5e0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f5e0-109">Remarks</span></span>  
 <span data-ttu-id="1f5e0-110">Birden fazla dosyadan içeri aktarmak için içeren bir **/reference** her dosya için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-110">To import from more than one file, include a **/reference** option for each file.</span></span>  
  
 <span data-ttu-id="1f5e0-111">İçeri aktardığınız dosyaları bir bildirim içermelidir; çıktı dosyası biriyle derlenmiştir gerekir [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1f5e0-111">The files you import must contain a manifest; the output file must have been compiled with one of the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="1f5e0-112">**/r** kısa biçimi olan **/reference**.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-112">**/r** is the short form of **/reference**.</span></span>  
  
 <span data-ttu-id="1f5e0-113">Kullanım [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) bir derleme bildirimi içermeyen bir çıktı dosyasından meta verileri almak için.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-113">Use [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="1f5e0-114">Başka bir derlemeye (B derlemesi) başvuran bir derlemeye (a derlemesi) başvurursanız, derleme B referansı gerekir:</span><span class="sxs-lookup"><span data-stu-id="1f5e0-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="1f5e0-115">Derleme A'dan kullandığınız bir tür bir türden devralır veya derleme B'deki bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="1f5e0-116">Alan, özellik, olay veya bir dönüş türü veya parametresi türü derleme B'deki sahip yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="1f5e0-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="1f5e0-117">Kullanım [/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-117">Use [/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="1f5e0-118">**/Lib** konuda ayrıca derleyicinin derlemeleri aradığı dizinleri anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-118">The **/lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="1f5e0-119">Derlemedeki ve bir modüldeki bir türü tanımak derleyici için sırayla türünün bir örneği tanımlayarak yapabilirsiniz türünü çözümlemek üzere zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="1f5e0-120">Derleyici ilişkin bir derlemede tür adları çözümlemek için diğer yolu vardır: bir bütünleştirilmiş türünden devralan, örneğin, tür adı sonra derleyici tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="1f5e0-121">Bazen bir derlemenin içinde aynı bileşeninin iki farklı sürümü başvurmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="1f5e0-122">Bunu yapmak için üstündeki takma alt seçeneği kullanmanız **/reference** geçiş iki dosya arasında ayrım yapmak her bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-122">To do this, use the alias suboption on the **/reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="1f5e0-123">Bu diğer ad niteleyicisi olarak bileşen adı için kullanılacak ve dosyalardan birini bileşeni çözer.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="1f5e0-124">Yaygın olarak kullanılan .NET Framework derlemelerine hangi başvuruları, csc yanıt (.rsp) dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="1f5e0-125">Kullanmak [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Derleyicinin csc.rsp kullanmasını istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-125">Use [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f5e0-126">Visual Studio'da kullanın **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="1f5e0-127">Daha fazla bilgi için bkz: [nasıl yapılır: başvuru ekleme veya kaldırma başvuru Yöneticisi'ni kullanarak](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span><span class="sxs-lookup"><span data-stu-id="1f5e0-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="1f5e0-128">Kullanarak başvurular ekleme arasındaki eşdeğer davranışı sağlamak için `/reference` ve kullanarak başvurular ekleme **Başvuru Ekle** iletişim kutusu, kümesi **birlikte çalışma türlerini katıştır** özelliğine**Yanlış** eklediğiniz derleme için.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-128">To ensure equivalent behavior between adding references by using `/reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="1f5e0-129">**Doğru** özellik için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f5e0-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f5e0-130">Example</span></span>  
 <span data-ttu-id="1f5e0-131">Bu örnek nasıl kullanılacağını gösterir [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="1f5e0-132">Kaynak dosyasını derleyin ve meta verilerini içeri aktarın `grid.dll` ve `grid20.dll`, hangi önceden derlenmiş olan.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`,which have been compiled previously.</span></span> <span data-ttu-id="1f5e0-133">İki DLLs aynı bileşenin ayrı sürümlerini içerir ve iki kullandığınız **/reference** kaynak dosyasını derlemek için diğer seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-133">The two DLLs contain separate versions of the same component, and you use two **/reference** with alias options to compile the source file.</span></span> <span data-ttu-id="1f5e0-134">Seçenekler şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="1f5e0-134">The options look like this:</span></span>  
  
 <span data-ttu-id="1f5e0-135">/Reference:GridV1=Grid.dll ve /reference:GridV2=grid20.dll</span><span class="sxs-lookup"><span data-stu-id="1f5e0-135">/reference:GridV1=grid.dll and /reference:GridV2=grid20.dll</span></span>  
  
 <span data-ttu-id="1f5e0-136">Bu dış diğer adlar "GridV1" ve "extern ifade yoluyla programınıza kullandığınız GridV2," ayarlar:</span><span class="sxs-lookup"><span data-stu-id="1f5e0-136">This sets up the external aliases "GridV1" and "GridV2," which you use in your program by means of an extern statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="1f5e0-137">Bunu yaptıktan sonra bu gibi denetim adına GridV1 ekleyerek kılavuz denetimine grid.dll öğesinden başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="1f5e0-137">Once this is done, you can refer to the grid control from grid.dll by prefixing the control name with GridV1, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="1f5e0-138">Buna ek olarak, Denetim adına GridV2 ile bu ekleyerek kılavuz denetimine grid20.dll öğesinden başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="1f5e0-138">In addition, you can refer to the grid control from grid20.dll by prefixing the control name with GridV2 like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="1f5e0-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f5e0-139">See Also</span></span>  
 [<span data-ttu-id="1f5e0-140">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1f5e0-140">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1f5e0-141">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="1f5e0-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
