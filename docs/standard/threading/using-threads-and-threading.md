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
ms.openlocfilehash: 80eb4c3bb98acdd1f83dbf5bcf57b2f7b295742b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="ac862-102">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="ac862-102">Using Threads and Threading</span></span>
<span data-ttu-id="ac862-103">Bu bölümdeki konular, oluşturulmasını ve yönetimini yönetilen iş parçacığı, yönetilen iş parçacığı veri geçirmek ve geri sonuçlar almak nasıl ve iş parçacıklarını yok ve işlemek nasıl ele bir <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="ac862-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac862-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac862-104">In This Section</span></span>  
 [<span data-ttu-id="ac862-105">İş parçacığı oluşturma ve başlangıç zamanında veri geçirme</span><span class="sxs-lookup"><span data-stu-id="ac862-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="ac862-106">Açıklanır ve nasıl yeni iş parçacıklarına veri geçirme ve veri geri alma dahil olmak üzere yönetilen iş parçacığı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac862-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="ac862-107">Duraklatma ve iş parçacıklarını sürdürme</span><span class="sxs-lookup"><span data-stu-id="ac862-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="ac862-108">Duraklatma ve sürdürme yönetilen iş parçacığı ayrımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ac862-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="ac862-109">İş parçacıklarını yok etme</span><span class="sxs-lookup"><span data-stu-id="ac862-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="ac862-110">Yönetilen iş parçacığı ve nasıl ele alınacağını yok etme, ayrımlar anlatılmaktadır bir <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="ac862-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="ac862-111">İş parçacıklarını zamanlama</span><span class="sxs-lookup"><span data-stu-id="ac862-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="ac862-112">İş parçacığı öncelikleri ve iş parçacığı planlama nasıl etkilediklerini anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac862-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac862-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ac862-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="ac862-114">Başvuru belgelerine sağlar <xref:System.Threading.Thread> yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="ac862-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="ac862-115">Başvuru belgelerine sağlar <xref:System.Threading.ThreadStart> parametresiz iş parçacığı yordamları temsil eden temsilci.</span><span class="sxs-lookup"><span data-stu-id="ac862-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="ac862-116">Güçlü yazarak rağmen olmadan iş parçacığı yordamı için veri iletmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac862-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac862-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ac862-117">Related Sections</span></span>  
 [<span data-ttu-id="ac862-118">İş parçacıkları ve iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ac862-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="ac862-119">Yönetilen iş parçacığı oluşturma giriş bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac862-119">Provides an introduction to managed threading.</span></span>
