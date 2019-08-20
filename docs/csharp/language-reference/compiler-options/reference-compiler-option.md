---
title: -Reference (C# derleyici seçenekleri)
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
ms.openlocfilehash: 247fb222eaacdb5ee60df2dded3a857f0395eb34
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606578"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="3d75b-102">-Reference (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="3d75b-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="3d75b-103">**-Reference** seçeneği, derleyicinin belirtilen dosyadaki [ortak](../keywords/public.md) tür bilgilerini geçerli projeye almasına ve böylece belirtilen derleme dosyalarından meta verilere başvurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3d75b-103">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d75b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d75b-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d75b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d75b-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3d75b-106">Bir derleme bildirimi içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3d75b-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="3d75b-107">Birden fazla dosyayı içeri aktarmak için her dosya için ayrı bir **başvuru** seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3d75b-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="3d75b-108">Derlemedeki tüm C# ad alanlarını içerecek bir kök ad alanını temsil edecek geçerli bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="3d75b-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d75b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d75b-109">Remarks</span></span>  
 <span data-ttu-id="3d75b-110">Birden fazla dosyadan içeri aktarmak için her dosya için bir **-Reference** seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3d75b-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="3d75b-111">İçeri aktardığınız dosyaların bir bildirim içermesi gerekir; çıkış dosyası [-target: Module](./target-module-compiler-option.md)dışındaki [-target](./target-compiler-option.md) seçeneklerinden biriyle derlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d75b-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3d75b-112">**-r** **-Reference**öğesinin kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="3d75b-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="3d75b-113">Derleme bildirimi içermeyen bir çıkış dosyasından meta verileri içeri aktarmak için [-addmodule](./addmodule-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-113">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="3d75b-114">Başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvurdıysanız, şu durumlarda derleme B 'ye başvurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3d75b-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="3d75b-115">Derleme A 'dan kullandığınız tür bir türden devralır veya derleme B 'den bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="3d75b-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="3d75b-116">B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3d75b-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="3d75b-117">Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-lib](./lib-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-117">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="3d75b-118">**-Lib** konusu Ayrıca derleyicinin derlemeleri arayacağı dizinleri de açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d75b-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="3d75b-119">Derleyicinin bir derlemede değil bir derlemede bir tür tanımasını sağlamak için, türün bir örneğini tanımlayarak yapabileceğiniz, türü çözümlemeye zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d75b-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="3d75b-120">Derleyici için bir derlemede tür adlarını çözümlemek için başka yollar vardır: Örneğin, derlemedeki bir türden kalýtýmla, tür adı daha sonra derleyici tarafından tanınacaktır.</span><span class="sxs-lookup"><span data-stu-id="3d75b-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="3d75b-121">Bazen aynı bileşenin iki farklı sürümüne tek bir derlemede başvurulmasý gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d75b-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="3d75b-122">Bunu yapmak için, iki Dosya arasında ayrım yapmak üzere her bir dosya için **-Reference** anahtarındaki diğer ad alt öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="3d75b-123">Bu diğer ad, bileşen adı için bir niteleyici olarak kullanılacak ve dosyalardan birindeki bileşene çözümlencektir.</span><span class="sxs-lookup"><span data-stu-id="3d75b-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="3d75b-124">Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Csc yanıt (. rsp) dosyası varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d75b-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="3d75b-125">Derleyicinin Csc. rsp kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-125">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d75b-126">Visual Studio 'da **Başvuru Ekle** iletişim kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="3d75b-127">Daha fazla bilgi için [nasıl yapılır: Başvuru Yöneticisi 'Ni](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)kullanarak başvuruları ekleyin veya kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="3d75b-128">`-reference` **Başvuru Ekle** iletişim kutusunu kullanarak başvurular ekleme ve başvuruları ekleme arasındaki denk davranışı sağlamak için, eklemekte olduğunuz derleme için **birlikte çalışma türlerini katıştır** özelliğini **false** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="3d75b-129">Özellik için varsayılan değer **true** 'dur.</span><span class="sxs-lookup"><span data-stu-id="3d75b-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d75b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d75b-130">Example</span></span>  
 <span data-ttu-id="3d75b-131">Bu örnek, [extern diğer ad](../keywords/extern-alias.md) özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d75b-131">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="3d75b-132">Kaynak dosyayı derleyip daha önce derlenen ve `grid.dll` `grid20.dll`' dan meta verileri içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="3d75b-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="3d75b-133">İki DLL aynı bileşenin ayrı sürümlerini içerir ve kaynak dosyayı derlemek için diğer ad seçenekleriyle iki **başvuru** kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3d75b-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="3d75b-134">Seçenekler şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="3d75b-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="3d75b-135">Bu, programınızda bir `GridV1` `extern` deyime göre kullandığınız `GridV2`dış diğer adları ve ' ı ayarlar:</span><span class="sxs-lookup"><span data-stu-id="3d75b-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="3d75b-136">Bu işlem tamamlandıktan sonra, aşağıdaki gibi denetim `grid.dll` `GridV1`adının önüne ekleyerek kılavuz denetimine başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d75b-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="3d75b-137">Ayrıca, aşağıdaki `grid20.dll` `GridV2` gibi denetim adının önüne ekleyerek kılavuz denetimine başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d75b-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="3d75b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d75b-138">See also</span></span>

- [<span data-ttu-id="3d75b-139">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="3d75b-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3d75b-140">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="3d75b-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
