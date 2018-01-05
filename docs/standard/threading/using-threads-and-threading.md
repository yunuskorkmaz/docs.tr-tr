---
title: "İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5bed13950a29cfa787ef8c9eb2608c6d74dfd49f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="15789-102">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="15789-102">Using Threads and Threading</span></span>
<span data-ttu-id="15789-103">Bu bölümdeki konular, oluşturulmasını ve yönetimini yönetilen iş parçacığı, yönetilen iş parçacığı veri geçirmek ve geri sonuçlar almak nasıl ve iş parçacıklarını yok ve işlemek nasıl ele bir <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="15789-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15789-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="15789-104">In This Section</span></span>  
 [<span data-ttu-id="15789-105">Başlatma Zamanında İş Parçacığı Oluşturma ve Veri Geçirme</span><span class="sxs-lookup"><span data-stu-id="15789-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="15789-106">Açıklanır ve nasıl yeni iş parçacıklarına veri geçirme ve veri geri alma dahil olmak üzere yönetilen iş parçacığı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="15789-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="15789-107">İş Parçacıklarını Duraklatma ve Sürdürme</span><span class="sxs-lookup"><span data-stu-id="15789-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="15789-108">Duraklatma ve sürdürme yönetilen iş parçacığı ayrımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="15789-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="15789-109">İş Parçacıklarını Yok Etme</span><span class="sxs-lookup"><span data-stu-id="15789-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="15789-110">Yönetilen iş parçacığı ve nasıl ele alınacağını yok etme, ayrımlar anlatılmaktadır bir <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="15789-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="15789-111">İş Parçacıklarını Zamanlama</span><span class="sxs-lookup"><span data-stu-id="15789-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="15789-112">İş parçacığı öncelikleri ve iş parçacığı planlama nasıl etkilediklerini anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15789-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="15789-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="15789-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="15789-114">Başvuru belgelerine sağlar <xref:System.Threading.Thread> yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="15789-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="15789-115">Başvuru belgelerine sağlar <xref:System.Threading.ThreadStart> parametresiz iş parçacığı yordamları temsil eden temsilci.</span><span class="sxs-lookup"><span data-stu-id="15789-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="15789-116">Güçlü yazarak rağmen olmadan iş parçacığı yordamı için veri iletmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="15789-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15789-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="15789-117">Related Sections</span></span>  
 [<span data-ttu-id="15789-118">İş Parçacıkları ve İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15789-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="15789-119">Yönetilen iş parçacığı oluşturma giriş bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="15789-119">Provides an introduction to managed threading.</span></span>
