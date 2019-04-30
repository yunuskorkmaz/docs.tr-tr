---
title: 'Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0968443af28e2d403b08a1af50846e7a1369db49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751754"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="b2bde-102">Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma</span><span class="sxs-lookup"><span data-stu-id="b2bde-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="b2bde-103">Bir yalıtılmış depolama bir veri bölmesi sanal dosya sisteminde kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b2bde-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="b2bde-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Sınıfı bir dizi bir yalıtılmış depolama ile etkileşim kurmak için yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2bde-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="b2bde-105">Oluşturma ve depoları almak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> üç statik yöntemler sağlar:</span><span class="sxs-lookup"><span data-stu-id="b2bde-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
- <span data-ttu-id="b2bde-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> Kullanıcı ve derlemeye göre yalıtılmış depolama döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2bde-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
- <span data-ttu-id="b2bde-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> etki alanı ve derlemeye göre yalıtılır depolama döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2bde-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="b2bde-108">Her iki yöntem içinden çağrılır koda ait bir depolama alın.</span><span class="sxs-lookup"><span data-stu-id="b2bde-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
- <span data-ttu-id="b2bde-109">Statik yöntem <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> kapsam parametre birleşimi geçirerek belirtilen bir yalıtılmış depolama döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2bde-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="b2bde-110">Aşağıdaki kod, kullanıcı, derleme ve etki alanı tarafından izole edilmiş bir depo döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2bde-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="b2bde-111">Kullanabileceğiniz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> gezici kullanıcı profili ile mağaza Dolaşımda olması belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2bde-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="b2bde-112">Bu nasıl oluşturulacağı hakkında daha fazla bilgi için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="b2bde-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="b2bde-113">Farklı bütünleştirilmiş kodlarında alınan yalıtılmış depoları, varsayılan olarak, farklı mağazalarda olur.</span><span class="sxs-lookup"><span data-stu-id="b2bde-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="b2bde-114">Derleme veya etki alanı kanıt parametrelerinde olarak geçirerek farklı bir derleme veya etki alanının depoya erişebilir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2bde-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="b2bde-115">Bu, uygulama etki alanı kimliği tarafından yalıtılmış depolamaya erişmek için izin gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="b2bde-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="b2bde-116">Daha fazla bilgi için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="b2bde-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="b2bde-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, Ve <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemleri döndürür bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesne.</span><span class="sxs-lookup"><span data-stu-id="b2bde-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="b2bde-118">Hangi yalıtım türü durumunuza en uygun olduğuna karar vermenize yardımcı olmak için bkz: [türleri, yalıtım](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="b2bde-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="b2bde-119">Bir yalıtılmış depolama dosyası nesne varsa, okuma, yazma, oluşturmak için yalıtılmış depolama yöntemleri kullanın ve dosya ve dizinleri silin.</span><span class="sxs-lookup"><span data-stu-id="b2bde-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="b2bde-120">Kod geçirme dan engelleyen bir mekanizma bulunmamaktadır bir <xref:System.IO.IsolatedStorage.IsolatedStorageFile> , kod nesne deposu almak için yeterli erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="b2bde-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="b2bde-121">Etki alanı ve derlemeye kimlikleri ve yalıtılmış depolama izinleri yalnızca başvuru olduğunda denetlenir bir <xref:System.IO.IsolatedStorage.IsolatedStorage> nesnesi elde edilir, normalde <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, veya <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2bde-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="b2bde-122">Başvurular koruma <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnedir, bu nedenle, sorumluluğu bu başvuruları kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="b2bde-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2bde-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2bde-123">Example</span></span>  
 <span data-ttu-id="b2bde-124">Aşağıdaki kod, kullanıcı ve derlemeye göre yalıtılır mağaza alma bir sınıfın basit bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2bde-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="b2bde-125">Kod ekleyerek kullanıcı, etki alanı ve derlemeye göre yalıtılır bir depo almak için değiştirilebilir <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> bağımsız değişkenler için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> yöntemi geçirir.</span><span class="sxs-lookup"><span data-stu-id="b2bde-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="b2bde-126">Kod çalıştırdıktan sonra bir deposuna yazarak oluşturulduğunu doğrulayabilirsiniz **StoreAdm/List** komut satırına.</span><span class="sxs-lookup"><span data-stu-id="b2bde-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="b2bde-127">Bu çalıştırır [yalıtılmış depolama aracı (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) ve tüm yalıtılmış geçerli kullanıcı için depolar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2bde-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b2bde-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bde-128">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="b2bde-129">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="b2bde-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="b2bde-130">Yalıtım Türleri</span><span class="sxs-lookup"><span data-stu-id="b2bde-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)
- [<span data-ttu-id="b2bde-131">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="b2bde-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
