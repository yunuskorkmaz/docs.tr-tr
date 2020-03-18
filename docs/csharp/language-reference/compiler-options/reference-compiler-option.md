---
title: -referans (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 3e6a999d528be111ba2b92886f4e6e3ebf185d5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173672"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="04a18-102">-referans (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="04a18-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="04a18-103">**-başvuru** seçeneği derleyicinin belirtilen dosyadaki [genel](../keywords/public.md) tür bilgilerini geçerli projeye aktararak belirtilen derleme dosyalarından meta verilere başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="04a18-103">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04a18-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="04a18-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="04a18-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="04a18-106">Bir derleme bildirimi içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="04a18-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="04a18-107">Birden fazla dosya almak için, her dosya için ayrı bir **başvuru** seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04a18-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="04a18-108">Derlemedeki tüm ad alanlarını içeren bir kök ad alanını temsil edecek geçerli bir C# tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="04a18-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04a18-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04a18-109">Remarks</span></span>  
 <span data-ttu-id="04a18-110">Birden fazla dosyadan içe almak için her dosya için bir **-başvuru** seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04a18-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="04a18-111">İçe aktardığınız dosyalar bir bildirim içermelidir; çıktı dosyası [-target:module](./target-module-compiler-option.md)dışındaki [-hedef](./target-compiler-option.md) seçeneklerinden biriyle derlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04a18-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="04a18-112">**-r** **-referansKısa**şeklidir.</span><span class="sxs-lookup"><span data-stu-id="04a18-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="04a18-113">Derleme bildirimi içermeyen bir çıktı dosyasından meta verileri almak için [-addmodule'ı](./addmodule-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="04a18-113">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="04a18-114">Başka bir derlemeye (B Derlemesi) başvuran bir derlemeye (A Derlemesi) başvurursanız, aşağıdaki ler varsa B Derlemesi'ne başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="04a18-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="04a18-115">A Derlemesi'nden kullandığınız bir tür, bir türden devralır veya B Derlemesi'nden bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="04a18-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="04a18-116">B derlemesinden iade türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="04a18-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="04a18-117">Derleme başvurularınızdan birinin veya daha fazlasının bulunduğu dizini belirtmek için [-lib'i](./lib-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="04a18-117">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="04a18-118">**-lib** konusu, derleyicinin derlemeleri aradığı dizinleri de tartışır.</span><span class="sxs-lookup"><span data-stu-id="04a18-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="04a18-119">Derleyicinin bir derlemedeki bir türü modülde değil, tanıyabilmesi için, türün bir örneğini tanımlayarak yapabileceğiniz türü çözmeye zorlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a18-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="04a18-120">Derleyici için bir derlemede tür adlarını çözmenin başka yolları da vardır: örneğin, bir derlemedeki bir türden devralırsanız, tür adı derleyici tarafından tanınAcaktır.</span><span class="sxs-lookup"><span data-stu-id="04a18-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="04a18-121">Bazen aynı bileşenin iki farklı sürümüne tek bir derleme içinden başvurmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a18-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="04a18-122">Bunu yapmak için, iki dosyayı birbirinden ayırmak için her dosya için **-başvuru** anahtarındaki diğer ad alt seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="04a18-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="04a18-123">Bu diğer ad, bileşen adı için bir niteleyici olarak kullanılır ve dosyalardan birinde bileşene çözülür.</span><span class="sxs-lookup"><span data-stu-id="04a18-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="04a18-124">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran csc yanıtı (.rsp) dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04a18-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="04a18-125">Derleyicinin csc.rsp kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="04a18-125">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04a18-126">Visual Studio'da **Başvuru Ekle** iletişim kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="04a18-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="04a18-127">Daha fazla bilgi için [bkz: Başvuru Yöneticisi'ni Kullanarak Başvuru Ekleme veya Kaldırma.](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)</span><span class="sxs-lookup"><span data-stu-id="04a18-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="04a18-128">**Başvuru Ekle** iletişim kutusunu kullanarak `-reference` başvuru ekleme ve ekleme arasında eşdeğer davranış sağlamak için, eklediğiniz derleme için **Embed Interop Türleri** özelliğini **False** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="04a18-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="04a18-129">**True,** özelliğin varsayılan değeridir.</span><span class="sxs-lookup"><span data-stu-id="04a18-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a18-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="04a18-130">Example</span></span>  
 <span data-ttu-id="04a18-131">Bu örnek, [extern diğer ad](../keywords/extern-alias.md) özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04a18-131">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="04a18-132">Kaynak dosyayı derler ve daha `grid.dll` `grid20.dll`önce derlenmiş olan meta verileri içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="04a18-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="04a18-133">İki DL aynı bileşenin ayrı sürümlerini içerir ve kaynak dosyayı derlemek için diğer ad seçenekleriyle iki **başvuru** kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="04a18-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="04a18-134">Seçenekler şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="04a18-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="04a18-135">Bu, harici diğer `GridV1` adları `GridV2`ve programınızda kullandığınız dış adları `extern` bir deyim le ayarlar:</span><span class="sxs-lookup"><span data-stu-id="04a18-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="04a18-136">Bu yapıldıktan sonra, aşağıdaki gibi denetim `grid.dll` adını `GridV1`önceden tutarak ızgara denetimine başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="04a18-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="04a18-137">Buna ek olarak, aşağıdaki `grid20.dll` `GridV2` gibi denetim adını öne leyerek ızgara denetimine başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="04a18-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="04a18-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a18-138">See also</span></span>

- [<span data-ttu-id="04a18-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="04a18-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="04a18-140">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="04a18-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
