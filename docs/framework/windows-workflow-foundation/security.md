---
title: Güvenlik
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: d82ad52dd24dbfcb66887693563b08c995baa63a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619492"
---
# <a name="security"></a><span data-ttu-id="09a7c-102">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="09a7c-102">Security</span></span>
<span data-ttu-id="09a7c-103">SQL iş akışı örneği Store, örnek durum bilgilerini kalıcı veritabanındaki erişim güvenliğini sağlamak için aşağıdaki veritabanı güvenlik rollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="09a7c-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="09a7c-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="09a7c-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="09a7c-105">Bu rol okuma ve yazma erişimi genel görünüm ve yürütme hakları katılan oluşturma, yükleme ve kaydetme örnekleri saklı yordamları.</span><span class="sxs-lookup"><span data-stu-id="09a7c-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="09a7c-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="09a7c-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="09a7c-107">Bu rol, genel görünümlerini salt okunur erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="09a7c-107">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="09a7c-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="09a7c-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="09a7c-109">Bu rol örneği etkinleştirme işlemine dahil olan saklı yordamları yürütme hakkı vardır.</span><span class="sxs-lookup"><span data-stu-id="09a7c-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="09a7c-110">Örnek etkinleştirme hakkında daha fazla bilgi için bkz: [örnek etkinleştirme](instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="09a7c-110">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="09a7c-111">Kullanıcı hesabında genel bir ana bilgisayar (iş akışı yönetimi hizmeti, gibi [!INCLUDE[dublin](../../../includes/dublin-md.md)]) çalışır, bu veritabanı rolüne eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="09a7c-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="09a7c-112">Windows Server App Fabric ile Kalıcılık depoları için güvenlik hakkında daha fazla bilgi için bkz. [App Fabric Kalıcılık depoları için güvenlik yapılandırması](https://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="09a7c-112">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](https://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="09a7c-113">Örnek deposunda kendi örnek veri erişimi olan bir istemci aynı örnek depodaki tüm diğer örneklerden erişebilir.</span><span class="sxs-lookup"><span data-stu-id="09a7c-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="09a7c-114">Örnek deposuna örnek düzeyinde belirten güvenlik izinleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="09a7c-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="09a7c-115">Farklı bir örnek deposu oluşturma ve erişimi için farklı mağazalarda farklı gruplar/kullanıcılar eşleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="09a7c-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
