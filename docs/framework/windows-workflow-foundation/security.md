---
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: cbfb82c2db329725d3445e1a88b54e01d5813f36
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348401"
---
# <a name="security"></a><span data-ttu-id="1f65a-102">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="1f65a-102">Security</span></span>
<span data-ttu-id="1f65a-103">SQL iş akışı örneği Store, örnek durum bilgilerini kalıcı veritabanındaki erişim güvenliğini sağlamak için aşağıdaki veritabanı güvenlik rollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f65a-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="1f65a-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="1f65a-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="1f65a-105">Bu rol okuma ve yazma erişimi genel görünüm ve yürütme hakları katılan oluşturma, yükleme ve kaydetme örnekleri saklı yordamları.</span><span class="sxs-lookup"><span data-stu-id="1f65a-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="1f65a-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="1f65a-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="1f65a-107">Bu rol, genel görünümlerini salt okunur erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="1f65a-107">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="1f65a-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="1f65a-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="1f65a-109">Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme hakkı vardır.</span><span class="sxs-lookup"><span data-stu-id="1f65a-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="1f65a-110">Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örnek etkinleştirme](instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="1f65a-110">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="1f65a-111">Genel bir ana bilgisayar (örneğin, Windows Server AppFabric barındırma özellikleri iş akışı yönetimi hizmeti) altında çalıştığı hesabın bu veritabanı rolüne eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1f65a-111">The user account under which a generic host (such as the Workflow Management Service of the hosting features of Windows Server AppFabric) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="1f65a-112">Windows Server App Fabric ile Kalıcılık depoları için güvenlik hakkında daha fazla bilgi için bkz. [App Fabric Kalıcılık depoları için güvenlik yapılandırması](https://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="1f65a-112">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](https://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1f65a-113">Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek depodaki tüm diğer örneklerden erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1f65a-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="1f65a-114">Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1f65a-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="1f65a-115">Farklı bir örnek deposu oluşturma ve erişimi için farklı mağazalarda farklı gruplar/kullanıcılar eşleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f65a-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
