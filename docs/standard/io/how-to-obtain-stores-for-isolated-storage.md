---
description: 'Daha fazla bilgi edinin: nasıl yapılır: yalıtılmış depolama için depoları alma'
title: 'Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 4d65eb23d4e6935b72dd32926c097f7cf0ab6b85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775597"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="a47c1-103">Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma</span><span class="sxs-lookup"><span data-stu-id="a47c1-103">How to: Obtain Stores for Isolated Storage</span></span>

<span data-ttu-id="a47c1-104">Yalıtılmış bir mağaza, bir veri bölmesi içinde sanal bir dosya sistemi sunar.</span><span class="sxs-lookup"><span data-stu-id="a47c1-104">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="a47c1-105"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>Sınıfı yalıtılmış bir mağaza ile etkileşim kurmak için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a47c1-105">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="a47c1-106">Mağaza oluşturmak ve almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntem sağlar:</span><span class="sxs-lookup"><span data-stu-id="a47c1-106">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
- <span data-ttu-id="a47c1-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Kullanıcı ve derleme tarafından yalıtılmış depolamayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a47c1-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
- <span data-ttu-id="a47c1-108"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> etki alanı ve derleme tarafından yalıtılmış depolamayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a47c1-108"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="a47c1-109">Her iki yöntem de çağrıldıkları koda ait bir depoyu alır.</span><span class="sxs-lookup"><span data-stu-id="a47c1-109">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
- <span data-ttu-id="a47c1-110">Static yöntemi, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametrelerinin bir birleşimi geçirerek belirtilen yalıtılmış bir depo döndürür.</span><span class="sxs-lookup"><span data-stu-id="a47c1-110">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="a47c1-111">Aşağıdaki kod, Kullanıcı, derleme ve etki alanı tarafından yalıtılmış bir depo döndürür.</span><span class="sxs-lookup"><span data-stu-id="a47c1-111">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="a47c1-112"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>Bir deponun bir dolaşım kullanıcı profiliyle dolaşımını belirtmek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47c1-112">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="a47c1-113">Bu ayarı ayarlama hakkında daha fazla bilgi için bkz. [yalıtım türleri](types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="a47c1-113">For details on how to set this up, see [Types of Isolation](types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="a47c1-114">Farklı derlemelerin içinden alınan yalıtılmış depolar, varsayılan olarak farklı depolardır.</span><span class="sxs-lookup"><span data-stu-id="a47c1-114">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="a47c1-115">Farklı bir derlemenin veya etki alanının deposuna, derleme veya etki alanı bulgusunda metodun parametrelerini geçirerek erişebilirsiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> .</span><span class="sxs-lookup"><span data-stu-id="a47c1-115">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="a47c1-116">Bu, uygulama etki alanı kimliğine göre yalıtılmış depolamaya erişmek için izin gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a47c1-116">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="a47c1-117">Daha fazla bilgi için bkz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> . yöntem aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="a47c1-117">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="a47c1-118"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> Ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a47c1-118">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="a47c1-119">Hangi yalıtım türünün durumunuza en uygun olduğuna karar vermenize yardımcı olması için bkz. [yalıtım türleri](types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="a47c1-119">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](types-of-isolation.md).</span></span> <span data-ttu-id="a47c1-120">Yalıtılmış bir depolama dosya nesneniz varsa, dosyaları ve dizinleri okumak, yazmak, oluşturmak ve silmek için yalıtılmış depolama yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47c1-120">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="a47c1-121">Kodun, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> deponun kendisini almak için yeterli erişimi olmayan koda bir nesne geçirilmesini engelleyen bir mekanizma yoktur.</span><span class="sxs-lookup"><span data-stu-id="a47c1-121">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="a47c1-122">Etki alanı ve derleme kimlikleri ve yalıtılmış depolama izinleri yalnızca <xref:System.IO.IsolatedStorage.IsolatedStorage> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> , genellikle, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> veya yönteminde bir nesne başvurusu elde edildiğinde denetlenir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> .</span><span class="sxs-lookup"><span data-stu-id="a47c1-122">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="a47c1-123">Bu nedenle, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Bu başvuruları kullanan kodun sorumluluğu, bu nedenle nesnelere başvuruları koruma.</span><span class="sxs-lookup"><span data-stu-id="a47c1-123">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a47c1-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a47c1-124">Example</span></span>  

 <span data-ttu-id="a47c1-125">Aşağıdaki kod, Kullanıcı ve derleme tarafından yalıtılmış bir depo elde eden bir sınıfa ilişkin basit bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a47c1-125">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="a47c1-126">Kod, <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> yöntemin geçirdiği bağımsız değişkenlere ekleyerek Kullanıcı, etki alanı ve derleme tarafından yalıtılmış bir depoyu almak üzere değiştirilebilir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> .</span><span class="sxs-lookup"><span data-stu-id="a47c1-126">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="a47c1-127">Kodu çalıştırdıktan sonra, komut satırına **Storeadm/List** yazarak bir deponun oluşturulduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a47c1-127">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="a47c1-128">Bu, [yalıtılmış depolama aracını (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) çalıştırır ve Kullanıcı için geçerli yalıtılmış tüm depoları listeler.</span><span class="sxs-lookup"><span data-stu-id="a47c1-128">This runs the [Isolated Storage tool (Storeadm.exe)](../../framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a47c1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a47c1-129">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="a47c1-130">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="a47c1-130">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="a47c1-131">Yalıtım Türleri</span><span class="sxs-lookup"><span data-stu-id="a47c1-131">Types of Isolation</span></span>](types-of-isolation.md)
- [<span data-ttu-id="a47c1-132">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="a47c1-132">Assemblies in .NET</span></span>](../assembly/index.md)
