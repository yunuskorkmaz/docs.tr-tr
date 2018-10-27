---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 1a5284915de739e95325234318842a4d1ab607be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135252"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="d0774-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="d0774-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="d0774-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="d0774-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0774-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0774-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d0774-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0774-105">Methods</span></span>  
 <span data-ttu-id="d0774-106">ServiceTimeoutsBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d0774-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0774-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0774-107">Properties</span></span>  
 <span data-ttu-id="d0774-108">ServiceTimeoutsBehavior sınıfı şu özelliğe sahip:</span><span class="sxs-lookup"><span data-stu-id="d0774-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="d0774-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="d0774-109">TransactionTimeout</span></span>  
 <span data-ttu-id="d0774-110">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="d0774-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="d0774-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0774-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0774-112">İçinde bir işlemin tamamlanması gereken süre.</span><span class="sxs-lookup"><span data-stu-id="d0774-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0774-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0774-113">Requirements</span></span>  
  
|<span data-ttu-id="d0774-114">MOF</span><span class="sxs-lookup"><span data-stu-id="d0774-114">MOF</span></span>|<span data-ttu-id="d0774-115">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d0774-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0774-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d0774-116">Namespace</span></span>|<span data-ttu-id="d0774-117">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d0774-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0774-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0774-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
