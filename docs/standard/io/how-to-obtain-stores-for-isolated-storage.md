---
title: "Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 61f183398c3f8c93ead965036e1edeb200dd8cb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="c3bd2-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma</span><span class="sxs-lookup"><span data-stu-id="c3bd2-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="c3bd2-103">Yalıtılmış depolamada sanal dosya sistemi veri bölme içinde kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="c3bd2-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıf, çeşitli bir yalıtılmış depolamada ile etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="c3bd2-105">Oluşturmak ve depolar, almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntemler sağlar:</span><span class="sxs-lookup"><span data-stu-id="c3bd2-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="c3bd2-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Kullanıcı ve derlemeye göre yalıtılmış depolama döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="c3bd2-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>etki alanı ve derleme tarafından yalıtılır depolama döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="c3bd2-108">Her iki yöntem, bunlar adlandırılır koduna ait bir depolama alın.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="c3bd2-109">Statik yöntemi <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametreleri bileşimini geçirerek belirtilen bir yalıtılmış depolamada döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="c3bd2-110">Aşağıdaki kod, kullanıcı, derleme ve etki alanı tarafından ayrılmış bir depolama döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="c3bd2-111">Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi bir gezici kullanıcı profili ile bir depolama dolaşan belirtin.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="c3bd2-112">Bu nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="c3bd2-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="c3bd2-113">İçinde farklı derlemeler alınan yalıtılmış depolar, varsayılan olarak, farklı depoları etkilenir.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="c3bd2-114">Derleme veya etki alanı kanıt parametrelerinde içinde geçirerek farklı derleme veya etki alanının deposuna erişebilecek <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="c3bd2-115">Yalıtılmış Depolama uygulama etki alanı kimliği tarafından erişim izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="c3bd2-116">Daha fazla bilgi için bkz: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi aşırı.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="c3bd2-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, Ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri döndürür bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="c3bd2-118">Hangi yalıtım türü durumunuz için en uygun olan karar vermenize yardımcı olmak için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="c3bd2-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="c3bd2-119">Yalıtılmış depolama dosya nesneyi sahip olduğunuzda, okuma, yazma, oluşturmak için yalıtılmış depolama yöntemleri kullanabilir ve dosyaları ve dizinleri silin.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="c3bd2-120">Kod gelen geçirme engeller hiçbir mekanizması bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kodunu nesnesine deposu almak için yeterli erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="c3bd2-121">Etki alanı ve derleme kimlikleri ve yalıtılmış depolama izinleri işaretli yalnızca başvuru olduğunda bir <xref:System.IO.IsolatedStorage.IsolatedStorage> nesne elde edilir, genellikle içinde <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="c3bd2-122">Başvurular koruma <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnedir, bu nedenle, bu başvuruları kullanan kodu sorumluluğudur.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3bd2-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3bd2-123">Example</span></span>  
 <span data-ttu-id="c3bd2-124">Aşağıdaki kod, kullanıcı ve derlemeye göre yalıtılmış bir mağaza alma bir sınıfın basit bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="c3bd2-125">Kullanıcı, etki alanı ve derleme tarafından ekleyerek yalıtılmış olduğundan bir depolama almak için kod değiştirilebilir <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> bağımsız değişkenler için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi geçirir.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="c3bd2-126">Kod çalıştırdıktan sonra bir depolama yazarak oluşturulduğunu doğrulayabilirsiniz **StoreAdm/List** komut satırında.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="c3bd2-127">Bu çalıştırır [yalıtılmış depolama aracı (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ve tüm yalıtılmış geçerli kullanıcı için depolar listeler.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c3bd2-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-128">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="c3bd2-129">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="c3bd2-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="c3bd2-130">Yalıtım Türleri</span><span class="sxs-lookup"><span data-stu-id="c3bd2-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)  
 [<span data-ttu-id="c3bd2-131">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="c3bd2-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
