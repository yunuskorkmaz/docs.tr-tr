---
description: 'Daha fazla bilgi edinin: güvenlik'
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 8f095292deac77c1c72cf87a93064569f7dab982
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798101"
---
# <a name="security"></a><span data-ttu-id="042b0-103">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="042b0-103">Security</span></span>

<span data-ttu-id="042b0-104">SQL Iş akışı örneği deposu, kalıcılık veritabanındaki örnek durum bilgilerine erişimi güvenli hale getirmek için aşağıdaki veritabanı güvenlik rollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="042b0-104">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="042b0-105">**System. Activities. Durableörneksistemi. InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="042b0-105">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="042b0-106">Bu rol, örnekleri oluşturma, yükleme ve kaydetme konusunda yer alan saklı yordamlarda ortak görünümlere ve yürütme haklarına okuma ve yazma erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="042b0-106">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="042b0-107">**System. Activities. Durableörneksistemi. InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="042b0-107">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="042b0-108">Bu rolün ortak görünümlere salt okuma erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="042b0-108">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="042b0-109">**System. Activities. Durableörnek oluşturma. WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="042b0-109">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="042b0-110">Bu rol, örnek etkinleştirme işleminde yer alan saklı yordamlara yönelik yürütme haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="042b0-110">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="042b0-111">Örnek etkinleştirme hakkında daha fazla bilgi için bkz. [örnek etkinleştirme](instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="042b0-111">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="042b0-112">Altında genel bir ana bilgisayarın (Windows Server AppFabric 'in barındırma özelliklerinin Iş akışı yönetim hizmeti gibi) çalıştırıldığı Kullanıcı hesabı, bu veritabanı rolüne eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="042b0-112">The user account under which a generic host (such as the Workflow Management Service of the hosting features of Windows Server AppFabric) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="042b0-113">Windows Server App Fabric ile Kalıcılık mağazalarına yönelik güvenlik hakkında daha fazla bilgi için bkz. [App Fabric 'Te Kalıcılık depoları Için güvenlik yapılandırması](/previous-versions/appfabric/ff431727(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="042b0-113">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](/previous-versions/appfabric/ff431727(v=azure.10))</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="042b0-114">Örnek deposundaki kendi örnek verilerine erişimi olan bir istemcinin aynı örnek deposundaki diğer tüm örneklere erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="042b0-114">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="042b0-115">Örnek deposu, örnek düzeyinde güvenlik izinleri belirtmeyi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="042b0-115">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="042b0-116">Farklı depolara erişim sağlamak için ayrı örnek depoları oluşturmanız ve farklı grupları/kullanıcıları eşlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="042b0-116">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
