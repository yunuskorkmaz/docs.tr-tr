---
description: Daha fazla bilgi için bkz. ServiceAppDomain
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 1ac32b1fbd88518ffb260be9dd3ed2adb88d211c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715645"
---
# <a name="serviceappdomain"></a><span data-ttu-id="089d1-103">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="089d1-103">ServiceAppDomain</span></span>

<span data-ttu-id="089d1-104">Bir hizmeti bir uygulama etki alanına eşler.</span><span class="sxs-lookup"><span data-stu-id="089d1-104">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089d1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="089d1-105">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="089d1-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="089d1-106">Methods</span></span>  

 <span data-ttu-id="089d1-107">ServiceAppDomain sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="089d1-107">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="089d1-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="089d1-108">Properties</span></span>  

 <span data-ttu-id="089d1-109">ServiceAppDomain sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="089d1-109">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="089d1-110">ref</span><span class="sxs-lookup"><span data-stu-id="089d1-110">ref</span></span>  

 <span data-ttu-id="089d1-111">Veri türü: hizmet</span><span class="sxs-lookup"><span data-stu-id="089d1-111">Data type: Service</span></span>  
<span data-ttu-id="089d1-112">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="089d1-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="089d1-113">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="089d1-113">Access type: Read-only</span></span>  
  
 <span data-ttu-id="089d1-114">Bu uygulama etki alanının hizmeti.</span><span class="sxs-lookup"><span data-stu-id="089d1-114">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="089d1-115">ref</span><span class="sxs-lookup"><span data-stu-id="089d1-115">ref</span></span>  

 <span data-ttu-id="089d1-116">Veri türü: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="089d1-116">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="089d1-117">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="089d1-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="089d1-118">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="089d1-118">Access type: Read-only</span></span>  
  
 <span data-ttu-id="089d1-119">Uygulama etki alanının özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="089d1-119">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="089d1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="089d1-120">Requirements</span></span>  
  
|<span data-ttu-id="089d1-121">MOF</span><span class="sxs-lookup"><span data-stu-id="089d1-121">MOF</span></span>|<span data-ttu-id="089d1-122">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="089d1-122">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="089d1-123">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="089d1-123">Namespace</span></span>|<span data-ttu-id="089d1-124">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="089d1-124">Defined in root\ServiceModel</span></span>|
