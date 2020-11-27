---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 243c9112dd9caf5c92ef77aa0f45b4b1e71a4e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273262"
---
# <a name="serviceappdomain"></a><span data-ttu-id="12b3f-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="12b3f-102">ServiceAppDomain</span></span>

<span data-ttu-id="12b3f-103">Bir hizmeti bir uygulama etki alanına eşler.</span><span class="sxs-lookup"><span data-stu-id="12b3f-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b3f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="12b3f-104">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="12b3f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="12b3f-105">Methods</span></span>  

 <span data-ttu-id="12b3f-106">ServiceAppDomain sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="12b3f-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="12b3f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="12b3f-107">Properties</span></span>  

 <span data-ttu-id="12b3f-108">ServiceAppDomain sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="12b3f-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="12b3f-109">ref</span><span class="sxs-lookup"><span data-stu-id="12b3f-109">ref</span></span>  

 <span data-ttu-id="12b3f-110">Veri türü: hizmet</span><span class="sxs-lookup"><span data-stu-id="12b3f-110">Data type: Service</span></span>  
<span data-ttu-id="12b3f-111">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="12b3f-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="12b3f-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="12b3f-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12b3f-113">Bu uygulama etki alanının hizmeti.</span><span class="sxs-lookup"><span data-stu-id="12b3f-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="12b3f-114">ref</span><span class="sxs-lookup"><span data-stu-id="12b3f-114">ref</span></span>  

 <span data-ttu-id="12b3f-115">Veri türü: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="12b3f-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="12b3f-116">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="12b3f-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="12b3f-117">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="12b3f-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12b3f-118">Uygulama etki alanının özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="12b3f-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b3f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12b3f-119">Requirements</span></span>  
  
|<span data-ttu-id="12b3f-120">MOF</span><span class="sxs-lookup"><span data-stu-id="12b3f-120">MOF</span></span>|<span data-ttu-id="12b3f-121">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12b3f-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="12b3f-122">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="12b3f-122">Namespace</span></span>|<span data-ttu-id="12b3f-123">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="12b3f-123">Defined in root\ServiceModel</span></span>|
