---
title: "Birden Çok Dosya Derlemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fead0a944b464ffd8f72dca6da33fd97404fe2d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="multifile-assemblies"></a><span data-ttu-id="954ba-102">Birden Çok Dosya Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="954ba-102">Multifile Assemblies</span></span>
<span data-ttu-id="954ba-103">Komut satırı derleyicileri kullanarak birden çok dosya derlemeleri oluşturabilir veya [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] Visual C++ ile.</span><span class="sxs-lookup"><span data-stu-id="954ba-103">You can create multifile assemblies using command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] with Visual C++.</span></span> <span data-ttu-id="954ba-104">Derleme bildirimi derlemesindeki bir dosya içermelidir.</span><span class="sxs-lookup"><span data-stu-id="954ba-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="954ba-105">Bir uygulamayı başlatır bütünleştirilmiş bir ana veya WinMain yöntemi gibi bir giriş noktası da içermelidir.</span><span class="sxs-lookup"><span data-stu-id="954ba-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>  
  
 <span data-ttu-id="954ba-106">Örneğin, iki kod modülleri, Client.cs ve Stringer.cs içeren bir uygulama olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="954ba-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="954ba-107">Stringer.cs oluşturur `myStringer` Client.cs kod tarafından başvurulan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="954ba-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="954ba-108">Client.cs içeren `Main` uygulamanın giriş noktasıdır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="954ba-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="954ba-109">Bu örnekte, iki kod modüllerini derleyin ve ardından uygulamayı başlatan derleme bildirimi içeren üçüncü bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="954ba-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="954ba-110">Derleme bildirimi her ikisi de başvuran `Client` ve `Stringer` modüller.</span><span class="sxs-lookup"><span data-stu-id="954ba-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="954ba-111">Derleme birden çok kod modülleri olsa bile, birden çok dosya derlemeleri yalnızca bir giriş noktası, olabilir.</span><span class="sxs-lookup"><span data-stu-id="954ba-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>  
  
 <span data-ttu-id="954ba-112">Birden fazla dosya derlemesi oluşturmak isteyebilirsiniz birkaç nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="954ba-112">There are several reasons you might want to create a multifile assembly:</span></span>  
  
-   <span data-ttu-id="954ba-113">Farklı dillerde yazılmış modüller birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="954ba-113">To combine modules written in different languages.</span></span> <span data-ttu-id="954ba-114">Birden fazla dosya derlemesi oluşturmak için en yaygın nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="954ba-114">This is the most common reason for creating a multifile assembly.</span></span>  
  
-   <span data-ttu-id="954ba-115">Bir uygulamayı yalnızca gerekli olduğunda indirilen modülde nadiren kullanılan türleri koyarak indirme en iyi duruma getirme.</span><span class="sxs-lookup"><span data-stu-id="954ba-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="954ba-116">Kullanarak yüklenecek uygulamaları oluşturuyorsanız `<object>` etiketi Microsoft Internet Explorer ile birden çok dosya derlemeleri oluşturmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="954ba-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="954ba-117">Bu senaryoda, bir dosyayı yalnızca derleme bildirimi içerir, kod modülleri ayrı da oluşturun.</span><span class="sxs-lookup"><span data-stu-id="954ba-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="954ba-118">Internet Explorer derleme bildirimi ilk indirir ve daha sonra herhangi bir ek modüller veya gerekli derlemeleri indirmek için çalışan iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="954ba-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="954ba-119">Derleme bildirimi içeren dosyası indirilirken, Internet Explorer kullanıcı girişine yanıt vermeyen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="954ba-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="954ba-120">Daha küçük derleme bildirimi içeren dosyayı, daha az zaman Internet Explorer yanıt vermeyen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="954ba-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>  
  
-   <span data-ttu-id="954ba-121">Kod modülleri birkaç Geliştiricileriniz tarafından geliştirilen birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="954ba-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="954ba-122">Her geliştirici bir derlemeye her kod modülü derleyebilirsiniz karşın, bu tüm modülleri birden çok dosya derlemeye yerleştirirseniz sunulmaz genel olarak açığa çıkarılması bazı türleri zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="954ba-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>  
  
 <span data-ttu-id="954ba-123">Derleme oluşturduktan sonra derleme bildirimi içeren dosyayı imzalayabilirsiniz (ve bu nedenle derleme), ya da dosyasını (ve derleme) güçlü bir ad verin ve genel derleme önbelleğinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="954ba-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="954ba-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="954ba-124">See Also</span></span>  
 [<span data-ttu-id="954ba-125">Nasıl yapılır: birden fazla dosya derleme</span><span class="sxs-lookup"><span data-stu-id="954ba-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="954ba-126">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="954ba-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
