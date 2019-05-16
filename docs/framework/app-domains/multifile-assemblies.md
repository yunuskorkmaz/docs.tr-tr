---
title: Birden Çok Dosya Derlemeleri
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 862fc7012c2c5c84a163d6716dfeb4b97f00cbcd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634172"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="369ea-102">Birden Çok Dosya Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="369ea-102">Multifile Assemblies</span></span>

<span data-ttu-id="369ea-103">Visual C++ ile komut satırı derleyicilerini veya Visual Studio kullanan çok dosyalı derlemeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="369ea-103">You can create multifile assemblies using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="369ea-104">Derlemedeki bir dosya, derleme bildirimi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="369ea-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="369ea-105">Bir uygulamayı başlatan bir derleme ana veya WinMain yöntemi gibi bir giriş noktası da içermelidir.</span><span class="sxs-lookup"><span data-stu-id="369ea-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>

<span data-ttu-id="369ea-106">Örneğin, iki kod modülleri, Client.cs ve Stringer.cs içeren bir uygulama olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="369ea-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="369ea-107">Stringer.cs oluşturur `myStringer` Client.cs kod tarafından başvurulan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="369ea-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="369ea-108">Client.cs içeren `Main` uygulamanın giriş noktası olan yöntem.</span><span class="sxs-lookup"><span data-stu-id="369ea-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="369ea-109">Bu örnekte, iki kod modülleri derleyin ve ardından uygulamayı başlatan derleme bildirimini içeren üçüncü bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="369ea-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="369ea-110">Derleme bildirimi hem de başvuruda `Client` ve `Stringer` modüller.</span><span class="sxs-lookup"><span data-stu-id="369ea-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>

> [!NOTE]
> <span data-ttu-id="369ea-111">Derlemenin birden çok kod modülleri olsa bile, birden çok dosya derlemeleri yalnızca bir giriş noktası olabilir.</span><span class="sxs-lookup"><span data-stu-id="369ea-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="369ea-112">Bir çoklu dosya derlemesi oluşturmak isteyebileceğiniz birkaç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="369ea-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="369ea-113">Farklı dillerde yazılan modülleri birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="369ea-113">To combine modules written in different languages.</span></span> <span data-ttu-id="369ea-114">Bir çoklu dosya derlemesi oluşturmak için en yaygın nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="369ea-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="369ea-115">Nadiren kullanılan türleri yalnızca gerektiğinde indirilen bir modülün yerleştirerek bir uygulamanın indirilmesini optimize için.</span><span class="sxs-lookup"><span data-stu-id="369ea-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="369ea-116">Kullanılarak indirilen uygulamalar oluşturuyorsanız `<object>` etiketi Microsoft Internet Explorer kullanarak, çok dosyalı derlemeler oluşturmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="369ea-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="369ea-117">Bu senaryoda, bir dosya yalnızca derleme bildirimi içeren kod modüllerinizi ayrı da oluşturun.</span><span class="sxs-lookup"><span data-stu-id="369ea-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="369ea-118">Internet Explorer, derleme bildirimi ilk indirir ve ardından herhangi bir ek modüller veya gerekli derlemeleri yüklemek için çalışan iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="369ea-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="369ea-119">Internet Explorer, derleme bildirimini içeren dosya karşıdan yüklenirken kullanıcı girişine yanıt vermeyen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="369ea-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="369ea-120">Daha küçük derleme bildirimini içeren dosyayı, daha az zaman Internet Explorer yanıt vermeyen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="369ea-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="369ea-121">Birden fazla geliştirici tarafından yazılan modülleri birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="369ea-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="369ea-122">Her geliştirici her kod modülü bir derlemenin içine derleyebilirsiniz olsa da, bu tüm modüller, bir çoklu dosya derlemesi koyarsanız gösterilmez genel olarak açığa için bazı türleri zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="369ea-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="369ea-123">Derleme oluşturduktan sonra derleme bildirimini içeren dosyayı imzalayabilirsiniz (ve bu nedenle derleme), dosya (ve derleme) güçlü bir ad verin ve genel derleme önbelleğinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="369ea-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="369ea-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="369ea-124">See also</span></span>

- [<span data-ttu-id="369ea-125">Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="369ea-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="369ea-126">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="369ea-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
