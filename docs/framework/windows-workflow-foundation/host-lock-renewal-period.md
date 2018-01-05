---
title: "Ana bilgisayar kilit yenileme süresi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7447d11e93cf33e69bc52d2cdec239c1be55bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="host-lock-renewal-period"></a><span data-ttu-id="9744a-102">Ana bilgisayar kilit yenileme süresi</span><span class="sxs-lookup"><span data-stu-id="9744a-102">Host Lock Renewal Period</span></span>
<span data-ttu-id="9744a-103">**Konak kilit yenileme süresini** özelliği SQL iş akışı örneği deposunun konak içinde bir iş akışı örneği üzerinde kendi kilit yeniler süre belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9744a-103">The **Host Lock Renewal Period** property of the SQL Workflow Instance Store lets you specify the time period within which the host renews its lock on a workflow instance.</span></span> <span data-ttu-id="9744a-104">Kilidi geçerli kaldığı için ana bilgisayar kilit yenileme süresini + 30 saniye.</span><span class="sxs-lookup"><span data-stu-id="9744a-104">The lock remains valid for Host Lock Renewal Period + 30 seconds.</span></span> <span data-ttu-id="9744a-105">Kilidi yenilemek ana bilgisayar başarısız olursa (diğer bir deyişle, kira süresini) kilidi bu süre içinde süresi dolar ve Kalıcılık sağlayıcı örneği kilidini açar.</span><span class="sxs-lookup"><span data-stu-id="9744a-105">If the host fails to renew the lock (in other words, extend the lease) within this time period, the lock expires and the persistence provider unlocks the instance.</span></span> <span data-ttu-id="9744a-106">Bu özellik için değer "ss: dd:" biçiminde TimeSpan türüdür.</span><span class="sxs-lookup"><span data-stu-id="9744a-106">The value for this property is of type TimeSpan of the form "hh:mm:ss".</span></span> <span data-ttu-id="9744a-107">Değer izin verilen minimum "00: 00:01" (1 saniye).</span><span class="sxs-lookup"><span data-stu-id="9744a-107">The minimum permitted value is "00:00:01" (1 second).</span></span> <span data-ttu-id="9744a-108">Bu özelliğin varsayılan değeri "00: 00:30" (30 saniye).</span><span class="sxs-lookup"><span data-stu-id="9744a-108">The default value of this property is "00:00:30" (30 seconds).</span></span>  
  
 <span data-ttu-id="9744a-109">Bu özellik, sahip bir iş akışı hizmeti örneği kilidini açabilir önce bir iş akışı hizmeti ana bilgisayarı nerede başarısız senaryolarda önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9744a-109">This property is significant in scenarios where a workflow service host fails before it can unlock a workflow service instance that it owns.</span></span> <span data-ttu-id="9744a-110">Böylece aynı bilgisayarda veya bir sunucu grubundaki başka bir bilgisayarda çalışan başka bir iş akışı hizmeti ana bilgisayarı elde edebilirsiniz kilit süresi dolduktan sonra bu senaryoda, kilit Kalıcılık veritabanındaki iş akışı hizmet örneği üzerinde Kalıcılık sağlayıcı tarafından kaldırılır Kilitle ve iş akışı hizmeti örneğinin son kalıcı durumunu kendi yürütülmesini Sürdür belleğe yükler.</span><span class="sxs-lookup"><span data-stu-id="9744a-110">In this scenario, the lock on the workflow service instance in the persistence database is removed by the persistence provider after the lock expires so that another workflow service host running on the same computer or another computer in a server farm can acquire the lock and load the workflow service instance into memory to resume its execution from its last persisted state.</span></span>  
  
 <span data-ttu-id="9744a-111">Bu özellik için daha yüksek bir değere ayarlamak, iş akışı uzun süre Kalıcılık veritabanında kilitlenmesine hizmet örnekleri neden olur ve bu nedenle örnek kurtarma son Kalıcılık noktasından geciktirir.</span><span class="sxs-lookup"><span data-stu-id="9744a-111">Setting a higher value for this property causes the workflow service instances to be locked in the persistence database for a longer time and therefore delays the recovery of the instance from the last persistence point.</span></span> <span data-ttu-id="9744a-112">Bu özellik için kısa bir süre ayarlama başarısız iş akışı hizmeti örneği hızlı bir şekilde almak için iş akışı hizmeti ana bilgisayarı yeni bir örneğini neden olur, ancak iş akışı hizmeti ana bilgisayarı ve SQL Server veritabanı için iş yükü artışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="9744a-112">Setting a short interval for this property causes the new instance of the workflow service host to pick up the failed workflow service instance quickly, but causes an increase in workload for the workflow service host and the SQL Server database.</span></span>  
  
 <span data-ttu-id="9744a-113">SQL iş akışı örneği deposuna düzenli aralıklarla uyanır ve onlar üzerinde süresi dolmuş kilitleri örnekleriyle algılar iç bir görev çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9744a-113">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects instances with expired locks on them.</span></span> <span data-ttu-id="9744a-114">Süresi dolan kilitleri örnekleriyle bulduğunda, böylece bir iş akışı ana almak ve bu örnekleri çalıştırmak RunnableInstances tabloda örnekleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9744a-114">When it finds instances with expired locks, it places the instances in the RunnableInstances table so that a workflow host can pick up and run these instances.</span></span>
