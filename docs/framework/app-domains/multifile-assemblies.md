---
title: Birden çok dosyalı derlemeler
description: Komut satırı derleyicilerini veya Visual C++ ile Visual Studio 'Yu kullanarak .NET 'i hedefleyen çok dosyalı derlemeler kullanın. Derlemedeki bir dosya, derleme bildirimini tutamalıdır.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: a5fb41b3b136a325e6b8658da521cba3176e929f
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104643"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="7ba4f-104">Birden çok dosyalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="7ba4f-104">Multifile assemblies</span></span>

<span data-ttu-id="7ba4f-105">Visual C++ komut satırı derleyicilerini veya Visual Studio 'Yu kullanarak .NET Framework hedefleyen çok dosyalı derlemeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-105">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="7ba4f-106">Derlemedeki bir dosyanın derleme bildirimini içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-106">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="7ba4f-107">Bir uygulamayı başlatan bir derleme, ya da yöntemi gibi bir giriş noktası içermelidir `Main` `WinMain` .</span><span class="sxs-lookup"><span data-stu-id="7ba4f-107">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="7ba4f-108">Örneğin, *Client.cs* ve *Stringer.cs*olmak üzere iki kod modülü içeren bir uygulamanız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-108">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="7ba4f-109">*Stringer.cs* , `myStringer` *Client.cs*içindeki kod tarafından başvurulan ad alanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-109">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="7ba4f-110">*Client.cs* , `Main` uygulamanın giriş noktası olan yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-110">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="7ba4f-111">Bu örnekte, iki kod modülünü derler ve ardından uygulamayı başlatan derleme bildirimini içeren üçüncü bir dosya oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-111">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="7ba4f-112">Derleme bildirimi hem *istemci* hem de *stru* modüllerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-112">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="7ba4f-113">Çok dosyalı derlemeler, derleme birden fazla kod modüllerine sahip olsa bile yalnızca bir giriş noktasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-113">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="7ba4f-114">Çok dosyalı bir derleme oluşturmak isteyebileceğiniz birkaç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="7ba4f-114">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="7ba4f-115">Farklı dillerde yazılmış modülleri birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-115">To combine modules written in different languages.</span></span> <span data-ttu-id="7ba4f-116">Bu, çok dosyalı bir derleme oluşturmanın en yaygın nedenidir.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-116">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="7ba4f-117">Nadiren kullanılan türleri yalnızca gerektiğinde indirilen bir modüle yerleştirerek, bir uygulamayı indirmeyi iyileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-117">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ba4f-118">`<object>`Microsoft Internet Explorer ile etiketi kullanılarak indirilecek uygulamalar oluşturuyorsanız, çok dosyalı derlemeler oluşturmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-118">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="7ba4f-119">Bu senaryoda, yalnızca derleme bildirimini içeren kod modüllerinizden ayrı bir dosya oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-119">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="7ba4f-120">Internet Explorer önce derleme bildirimini indirir ve ardından gereken ek modülleri veya derlemeleri indirmek için çalışan iş parçacıkları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-120">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="7ba4f-121">Derleme bildirimini içeren dosya indirilirken, Internet Explorer kullanıcı girişine yanıt vermez.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-121">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="7ba4f-122">Derleme bildirimini içeren dosya ne kadar küçükse Internet Explorer yanıt vermemeye karşı daha az zaman olur.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-122">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="7ba4f-123">Çeşitli geliştiriciler tarafından yazılan kod modüllerini birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-123">To combine code modules written by several developers.</span></span> <span data-ttu-id="7ba4f-124">Her geliştirici her kod modülünü bir derlemede derleyebilse de, bu, tüm modüller çok dosyalı bir derlemeye yerleştirilse, bazı türlerin herkese açık bir şekilde gösterilmesini zorlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-124">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="7ba4f-125">Derlemeyi oluşturduktan sonra, derleme bildirimini içeren dosyayı imzalayabilir ve bu nedenle derleme yapabilir ya da dosyaya ve derlemeye tanımlayıcı bir ad verebilir ve bunu genel derleme önbelleğine yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-125">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ba4f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ba4f-126">See also</span></span>

- [<span data-ttu-id="7ba4f-127">Nasıl yapılır: Birden çok dosyalı derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ba4f-127">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="7ba4f-128">Derlemeler ile programlama</span><span class="sxs-lookup"><span data-stu-id="7ba4f-128">Program with assemblies</span></span>](../../standard/assembly/index.md)
