---
title: "Güvenlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a17b77293d9a12fd3720fc54cb6c17a28a8c6ed0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security"></a><span data-ttu-id="b95ea-102">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b95ea-102">Security</span></span>
<span data-ttu-id="b95ea-103">SQL iş akışı örneği deposu Kalıcılık veritabanındaki örneği durumu bilgilere erişimi güvenli hale getirmek için aşağıdaki veritabanı güvenlik rollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b95ea-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="b95ea-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="b95ea-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="b95ea-105">Bu rol okuma ve yazma erişimi ortak görünümler ve yürütme hakları oynayan oluşturma, yükleme ve kaydetme örnekleri saklı yordamlar.</span><span class="sxs-lookup"><span data-stu-id="b95ea-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="b95ea-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="b95ea-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="b95ea-107">Bu rol ortak görünümler salt okunur erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b95ea-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="b95ea-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="b95ea-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="b95ea-109">Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme haklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="b95ea-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="b95ea-110">Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örneği etkinleştirme](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="b95ea-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="b95ea-111">Kullanıcı hesabında genel ana bilgisayar (iş akışı yönetimi hizmetini gibi [!INCLUDE[dublin](../../../includes/dublin-md.md)]) çalıştığında bu veritabanı rolüne eklenmesi.</span><span class="sxs-lookup"><span data-stu-id="b95ea-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="b95ea-112">bkz. Windows Server App Fabric ile kalıcılığı depoları için [App Fabric Kalıcılık depolarında için güvenlik yapılandırması](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="b95ea-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b95ea-113">Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek deposunda tüm diğer örnekleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="b95ea-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="b95ea-114">Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b95ea-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="b95ea-115">Ayrı örneği deposu oluşturma ve farklı gruplar/farklı mağazalarının kullanıcılarının erişimini eşleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="b95ea-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
