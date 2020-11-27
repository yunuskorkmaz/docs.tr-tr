---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 6e20556541b1aa48e7dfc6a8cde97e1bc477457e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273951"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="54e2a-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="54e2a-102">ServiceToEndpointAssociation</span></span>

<span data-ttu-id="54e2a-103">Bir hizmeti uç noktayla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="54e2a-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e2a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="54e2a-104">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="54e2a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54e2a-105">Methods</span></span>  

 <span data-ttu-id="54e2a-106">ServiceToEndpointAssociation sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="54e2a-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="54e2a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="54e2a-107">Properties</span></span>  

 <span data-ttu-id="54e2a-108">ServiceToEndpointAssociation sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="54e2a-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="54e2a-109">ref</span><span class="sxs-lookup"><span data-stu-id="54e2a-109">ref</span></span>  

 <span data-ttu-id="54e2a-110">Veri türü: hizmet</span><span class="sxs-lookup"><span data-stu-id="54e2a-110">Data type: Service</span></span>  
  
 <span data-ttu-id="54e2a-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54e2a-111">Access type: Read-only</span></span>  
<span data-ttu-id="54e2a-112">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="54e2a-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="54e2a-113">Uç noktayla ilişkili hizmet.</span><span class="sxs-lookup"><span data-stu-id="54e2a-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="54e2a-114">ref</span><span class="sxs-lookup"><span data-stu-id="54e2a-114">ref</span></span>  

 <span data-ttu-id="54e2a-115">Veri türü: uç nokta</span><span class="sxs-lookup"><span data-stu-id="54e2a-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="54e2a-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54e2a-116">Access type: Read-only</span></span>  
<span data-ttu-id="54e2a-117">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="54e2a-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="54e2a-118">Hizmetle ilişkili uç nokta.</span><span class="sxs-lookup"><span data-stu-id="54e2a-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54e2a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54e2a-119">Requirements</span></span>  
  
|<span data-ttu-id="54e2a-120">MOF</span><span class="sxs-lookup"><span data-stu-id="54e2a-120">MOF</span></span>|<span data-ttu-id="54e2a-121">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="54e2a-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="54e2a-122">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="54e2a-122">Namespace</span></span>|<span data-ttu-id="54e2a-123">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="54e2a-123">Defined in root\ServiceModel</span></span>|
