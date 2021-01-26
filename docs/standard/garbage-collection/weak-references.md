---
title: Zayıf Başvurular
description: .NET Atık toplayıcısının, uygulamanın nesneye erişmesine izin verirken bir nesne toplamasına izin veren zayıf başvurular hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
ms.openlocfilehash: a364435a5b0a480b0f6f70315e2d5465f61e6b5a
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794658"
---
# <a name="weak-references"></a><span data-ttu-id="0d248-103">Zayıf Başvurular</span><span class="sxs-lookup"><span data-stu-id="0d248-103">Weak References</span></span>

<span data-ttu-id="0d248-104">Çöp toplayıcı, uygulamanın kodu bu nesneye ulaşabilirken bir uygulama tarafından kullanılan bir nesneyi toplayamıyor.</span><span class="sxs-lookup"><span data-stu-id="0d248-104">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="0d248-105">Uygulamanın nesneye güçlü bir başvurusu olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="0d248-105">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="0d248-106">Zayıf bir başvuru, uygulamanın nesneye erişmesine hala izin verirken çöp toplayıcısının nesneyi toplamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d248-106">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="0d248-107">Zayıf bir başvuru yalnızca, kesin bir başvuru olmadığında nesne toplanana kadar belirsiz süre boyunca geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0d248-107">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="0d248-108">Zayıf bir başvuru kullandığınızda, uygulama nesneye bir güçlü başvuru elde edebilir ve bu da toplanmasını önler.</span><span class="sxs-lookup"><span data-stu-id="0d248-108">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="0d248-109">Ancak, güçlü bir başvurunun yeniden kurulmadan önce çöp toplayıcının nesneye her zaman ulaşmak her zaman risk vardır.</span><span class="sxs-lookup"><span data-stu-id="0d248-109">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="0d248-110">Zayıf başvurular, çok fazla bellek kullanan nesneler için yararlıdır ancak çöp toplama tarafından geri kazanıladıklarında kolayca yeniden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="0d248-110">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="0d248-111">Bir Windows Forms uygulamasındaki ağaç görünümünün, kullanıcıya karmaşık hiyerarşik bir seçenek seçeneği olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="0d248-111">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="0d248-112">Temel alınan veriler büyükse, Kullanıcı uygulamada başka bir şeyle ilişkili olduğunda ağacın bellekte tutulması verimsiz olur.</span><span class="sxs-lookup"><span data-stu-id="0d248-112">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="0d248-113">Kullanıcı uygulamanın başka bir kısmına geçtiğinde, <xref:System.WeakReference> ağaca bir zayıf başvuru oluşturmak ve tüm güçlü başvuruları yok etmek için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d248-113">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="0d248-114">Kullanıcı ağaca geri geçtiğinde, uygulama ağaca güçlü bir başvuru edinmeye çalışır ve başarılı olursa ağacın yeniden çözümlenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="0d248-114">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="0d248-115">Bir nesneyle zayıf bir başvuru oluşturmak için, <xref:System.WeakReference> izlenecek nesnenin örneğini kullanarak oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="0d248-115">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="0d248-116">Kod örneği için bkz <xref:System.WeakReference> . sınıf kitaplığı 'nda.</span><span class="sxs-lookup"><span data-stu-id="0d248-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="0d248-117">Kısa ve uzun zayıf başvurular</span><span class="sxs-lookup"><span data-stu-id="0d248-117">Short and Long Weak References</span></span>  

 <span data-ttu-id="0d248-118">Kısa bir zayıf başvuru veya uzun bir zayıf başvuru oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0d248-118">You can create a short weak reference or a long weak reference:</span></span>  
  
- <span data-ttu-id="0d248-119">Kısadır</span><span class="sxs-lookup"><span data-stu-id="0d248-119">Short</span></span>  
  
     <span data-ttu-id="0d248-120">Kısa bir zayıf başvurunun hedefi, `null` nesne çöp toplama tarafından geri kazanılır hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0d248-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="0d248-121">Zayıf başvuru, yönetilen bir nesnedir ve aynı diğer yönetilen nesneler gibi çöp toplamaya tabidir.</span><span class="sxs-lookup"><span data-stu-id="0d248-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="0d248-122">Kısa bir zayıf başvuru, için parametresiz oluşturucudur <xref:System.WeakReference> .</span><span class="sxs-lookup"><span data-stu-id="0d248-122">A short weak reference is the parameterless constructor for <xref:System.WeakReference>.</span></span>  
  
- <span data-ttu-id="0d248-123">Kalacağını</span><span class="sxs-lookup"><span data-stu-id="0d248-123">Long</span></span>  
  
     <span data-ttu-id="0d248-124">Nesnenin yöntemi çağrıldıktan sonra uzun bir zayıf başvuru tutulur <xref:System.Object.Finalize%2A> .</span><span class="sxs-lookup"><span data-stu-id="0d248-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="0d248-125">Bu, nesnenin yeniden oluşturulmasına izin verir, ancak nesnenin durumu öngörülemeyen olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="0d248-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="0d248-126">Uzun bir başvuruyu kullanmak için oluşturucuda belirtin `true` <xref:System.WeakReference> .</span><span class="sxs-lookup"><span data-stu-id="0d248-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="0d248-127">Nesnenin türünün bir <xref:System.Object.Finalize%2A> yöntemi yoksa, kısa zayıf başvuru işlevselliği uygulanır ve zayıf başvuru yalnızca hedef toplanana kadar geçerlidir. Bu, Sonlandırıcı çalıştıktan sonra herhangi bir zamanda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="0d248-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="0d248-128">Güçlü bir başvuru oluşturmak ve nesneyi tekrar kullanmak için, <xref:System.WeakReference.Target%2A> öğesinin özelliğini <xref:System.WeakReference> nesnesinin türüne atayın.</span><span class="sxs-lookup"><span data-stu-id="0d248-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="0d248-129"><xref:System.WeakReference.Target%2A>Özelliği döndürürse `null` nesne toplanmıştı; Aksi takdirde, uygulama kendisine güçlü bir başvuru içerdiğinden nesneyi kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d248-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="0d248-130">Zayıf başvuruları kullanmaya yönelik yönergeler</span><span class="sxs-lookup"><span data-stu-id="0d248-130">Guidelines for Using Weak References</span></span>  

 <span data-ttu-id="0d248-131">Yalnızca nesnenin durumu sonlandıralındıktan sonra tahmin edildiğinde uzun zayıf başvuruları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d248-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="0d248-132">Küçük nesnelere zayıf başvurular kullanmaktan kaçının çünkü işaretçinin kendisi büyük veya daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d248-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="0d248-133">Bellek yönetimi sorunlarına otomatik çözüm olarak zayıf başvuruları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="0d248-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="0d248-134">Bunun yerine, uygulamanızın nesnelerini işlemeye yönelik etkili bir önbelleğe alma ilkesi geliştirin.</span><span class="sxs-lookup"><span data-stu-id="0d248-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d248-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d248-135">See also</span></span>

- [<span data-ttu-id="0d248-136">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="0d248-136">Garbage Collection</span></span>](index.md)
