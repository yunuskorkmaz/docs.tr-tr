---
title: Derleme İçerikleri
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25594c55a5462c42611df7119dad37bd8a61cc2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149350"
---
# <a name="assembly-contents"></a><span data-ttu-id="2329b-102">Derleme İçerikleri</span><span class="sxs-lookup"><span data-stu-id="2329b-102">Assembly Contents</span></span>
<span data-ttu-id="2329b-103">Genel olarak, statik bir derleme dört öğeden oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="2329b-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="2329b-104">[Derleme bildirimi](../../../docs/framework/app-domains/assembly-manifest.md), derleme meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2329b-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="2329b-105">Tür metaverileri.</span><span class="sxs-lookup"><span data-stu-id="2329b-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="2329b-106">Türleri uygulayan Microsoft ara dili (MSIL) kodu.</span><span class="sxs-lookup"><span data-stu-id="2329b-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="2329b-107">Bir kaynak kümesi.</span><span class="sxs-lookup"><span data-stu-id="2329b-107">A set of resources.</span></span>  
  
 <span data-ttu-id="2329b-108">Yalnızca derleme bildirimi gereklidir, ancak derlemeye herhangi bir anlamlı işlevsellik sağlamak için türler veya kaynaklar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2329b-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="2329b-109">Bu öğeleri bir derleme içinde gruplandırmanın çeşitli yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="2329b-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="2329b-110">Tüm öğeleri, aşağıda gösterildiği şekilde tek bir fiziksel dosya halinde gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2329b-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 ![Tek Dosyalı derleme gösteren diyagram da MyAssembly.dll çağrılır.](./media/assembly-contents/single-file-assembly.gif)  
  
 <span data-ttu-id="2329b-112">Alternatif olarak, bir derlemenin öğeleri birkaç dosya içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2329b-112">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="2329b-113">Bu dosyalar derlenmiş kod modülleri (.netmodule), kaynaklar (örneğin .bmp veya .jpg dosyaları) veya uygulama tarafından gereken diğer dosyalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="2329b-113">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="2329b-114">Farklı dillerde yazılan modülleri birleştirmek ve az kullanılan türleri yalnızca gerektiğinde indirilen bir modülün içine yerleştirerek bir uygulamanın indirilmesini optimize etmek istediğinizde bir çoklu dosya derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2329b-114">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="2329b-115">Aşağıdaki görselde, kuramsal bir uygulamanın geliştiricisi bazı işlevsellik kodlarını farklı modüllere ayırmayı ve büyük bir kaynak dosyasını (bu durumda bir .bmp görüntüsü) orijinal dosyasında tutmayı seçmiştir.</span><span class="sxs-lookup"><span data-stu-id="2329b-115">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="2329b-116">.NET Framework, yalnızca kendine atıfta bulunulduğunda bir dosya indirdiğinden, seyrek atıfta bulunulan bir kodu uygulamadan farklı bir dosyada tutmak kod indirmeyi optimize eder.</span><span class="sxs-lookup"><span data-stu-id="2329b-116">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 ![Bir çoklu dosya derlemesi gösteren diyagram.](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
>  <span data-ttu-id="2329b-118">Bir çoklu dosya derlemesini oluşturan dosyalar dosya sistemi tarafından fiziksel olarak bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="2329b-118">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="2329b-119">Bunun yerine, derleme bildirimi aracılığıyla bağlanırlar ve ortak dil çalışma zamanı, bunları birer birim olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="2329b-119">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="2329b-120">Bu görselde, üç dosya da MyAssembly.dll içindeki derleme bildiriminde açıklandığı şekilde bir derlemede bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2329b-120">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="2329b-121">Dosya sistemi açısından üç ayrı dosyadırlar.</span><span class="sxs-lookup"><span data-stu-id="2329b-121">To the file system, they are three separate files.</span></span> <span data-ttu-id="2329b-122">Util.netmodule dosyası hiçbir derleme bilgisi içermediğinden, bu dosyanın bir modül olarak derlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2329b-122">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="2329b-123">Derleme oluşturulduğunda derleme bildirimi MyAssembly.dll içine eklenerek Util.netmodule ve Graphic.bmp ile olan ilişkisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2329b-123">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="2329b-124">Kaynak kodunuzu tasarlarken, uygulamanızın işlevselliğini bir veya daha fazla dosyaya nasıl ayıracağınız hakkında açık kararlar verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2329b-124">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="2329b-125">.NET Framework kodu tasarlarken, işlevselliği bir veya daha fazla derlemeye nasıl ayıracağınız hakkında da benzer kararlar verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2329b-125">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2329b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2329b-126">See also</span></span>

- [<span data-ttu-id="2329b-127">Ortak Dil Çalışma Zamanındaki Derlemeler</span><span class="sxs-lookup"><span data-stu-id="2329b-127">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="2329b-128">Derleme Bildirimi</span><span class="sxs-lookup"><span data-stu-id="2329b-128">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="2329b-129">Derleme Güvenliği Konuları</span><span class="sxs-lookup"><span data-stu-id="2329b-129">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
