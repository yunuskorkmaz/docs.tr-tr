---
title: "Zayıf Başvurular"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ca1331cc45f437882d38adba241e2767821de36
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="weak-references"></a><span data-ttu-id="15de2-102">Zayıf Başvurular</span><span class="sxs-lookup"><span data-stu-id="15de2-102">Weak References</span></span>
<span data-ttu-id="15de2-103">Uygulamanın kodu söz konusu nesne ulaşabilir sırada atık toplayıcı bir uygulama tarafından kullanılan bir nesne toplayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="15de2-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="15de2-104">Uygulama nesnesi için güçlü bir başvuru barındırıyor olarak sınıflandırılır.</span><span class="sxs-lookup"><span data-stu-id="15de2-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="15de2-105">Zayıf başvuru hala nesneye erişim uygulama verirken nesne toplamak için atık toplayıcı izin verir.</span><span class="sxs-lookup"><span data-stu-id="15de2-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="15de2-106">Zayıf başvuru yalnızca belirsiz süreyi güçlü başvuru mevcut nesne toplanır kadar sırasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="15de2-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="15de2-107">Zayıf başvuru kullandığınızda, uygulama, toplanmakta olan engelleyen nesne, güçlü bir başvuru elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15de2-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="15de2-108">Bununla birlikte, her zaman güçlü bir başvuru yeniden önce atık toplayıcı nesnesine ilk alırsınız riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="15de2-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="15de2-109">Zayıf başvurular çok miktarda bellek kullanır, ancak atık toplama tarafından kazanılır varsa kolaylıkla yeniden oluşturulabilir nesneler için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="15de2-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="15de2-110">Bir Windows Forms uygulaması ağaç görünümünde seçenekleri karmaşık hiyerarşik seçimine kullanıcıya görüntüler varsayalım.</span><span class="sxs-lookup"><span data-stu-id="15de2-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="15de2-111">Temel alınan veri büyükse, kullanıcı uygulamada başka bir şey ile söz konusu olduğunda ağaç bellekte tutma yetersiz olduğunu.</span><span class="sxs-lookup"><span data-stu-id="15de2-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="15de2-112">Kullanıcı başka bir uygulamanın parçası için hemen geçiş yaparken kullanabileceğiniz <xref:System.WeakReference> ağaç zayıf başvuru oluşturun ve tüm güçlü başvuruları yok etmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="15de2-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="15de2-113">Kullanıcı geri ağacına geçirildiğinde, uygulamanın ağaç güçlü bir başvuru almaya çalıştığında ve, başarılı olursa, ağaç yeniden oluşturuluyor önler.</span><span class="sxs-lookup"><span data-stu-id="15de2-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="15de2-114">Bir nesne zayıf bir başvuru oluşturmanız için oluşturduğunuz bir <xref:System.WeakReference> izlenmesi gereken nesne örneğini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="15de2-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="15de2-115">Ardından <xref:System.WeakReference.Target%2A> bu nesne ve özgün nesne başvurusu kümesi özelliğine `null`.</span><span class="sxs-lookup"><span data-stu-id="15de2-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="15de2-116">Kod örneği için bkz: <xref:System.WeakReference> Sınıf Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="15de2-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="15de2-117">Kısa ve uzun zayıf başvurular</span><span class="sxs-lookup"><span data-stu-id="15de2-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="15de2-118">Bir kısa zayıf bir başvuru veya uzun zayıf oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15de2-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="15de2-119">kısa</span><span class="sxs-lookup"><span data-stu-id="15de2-119">Short</span></span>  
  
     <span data-ttu-id="15de2-120">Başvuru hedef için bir kısa zayıf hale `null` zaman nesne iadesi atık toplama tarafından.</span><span class="sxs-lookup"><span data-stu-id="15de2-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="15de2-121">Zayıf başvuru kendisi yönetilen bir nesne değildir ve herhangi bir yönetilen nesne gibi çöp toplama tabidir.</span><span class="sxs-lookup"><span data-stu-id="15de2-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="15de2-122">Kısa zayıf için varsayılan oluşturucu başvurudur <xref:System.WeakReference>.</span><span class="sxs-lookup"><span data-stu-id="15de2-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="15de2-123">uzun</span><span class="sxs-lookup"><span data-stu-id="15de2-123">Long</span></span>  
  
     <span data-ttu-id="15de2-124">Uzun zayıf başvurusu nesnenin sonra tutulur <xref:System.Object.Finalize%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="15de2-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="15de2-125">Bu nesnenin yeniden oluşturulması için sağlar, ancak nesnenin durumunu öngörülemeyen kalır.</span><span class="sxs-lookup"><span data-stu-id="15de2-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="15de2-126">Uzun bir referans kullanmak üzere belirtmek `true` içinde <xref:System.WeakReference> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="15de2-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="15de2-127">Nesnenin türü yoksa bir <xref:System.Object.Finalize%2A> yöntemi, kısa zayıf başvuru işlevselliği uygular ve hedef toplanan kadar herhangi bir zaman sonra sonlandırıcıyı oluşabilen çalıştırılan yalnızca zayıf başvurusu geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="15de2-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="15de2-128">Güçlü bir başvuru kurmak ve nesne yeniden kullanmak için cast <xref:System.WeakReference.Target%2A> özelliği bir <xref:System.WeakReference> türde bir nesne.</span><span class="sxs-lookup"><span data-stu-id="15de2-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="15de2-129">Varsa <xref:System.WeakReference.Target%2A> özelliği döndürür `null`nesne toplanan; Aksi takdirde, uygulamanın yeniden elde, güçlü bir başvuru olduğundan nesne kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15de2-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="15de2-130">Zayıf başvurular kullanma için yönergeler</span><span class="sxs-lookup"><span data-stu-id="15de2-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="15de2-131">Uzun zayıf başvurular yalnızca gerekli olduğunda nesnenin durumunu sonlandırma sonra öngörülemeyen olduğu gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="15de2-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="15de2-132">İşaretçi olarak büyük veya daha büyük olabilir çünkü küçük nesnelere zayıf başvurular kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="15de2-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="15de2-133">Bellek yönetimi sorunları için otomatik bir çözüm olarak zayıf başvurular kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="15de2-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="15de2-134">Bunun yerine, uygulamanızın nesneleri işlemek için etkili bir önbellek İlkesi geliştirin.</span><span class="sxs-lookup"><span data-stu-id="15de2-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15de2-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15de2-135">See Also</span></span>  
 [<span data-ttu-id="15de2-136">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="15de2-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
