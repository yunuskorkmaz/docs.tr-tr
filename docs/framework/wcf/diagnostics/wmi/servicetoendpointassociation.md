---
description: 'Hakkında daha fazla bilgi edinin: ServiceToEndpointAssociation'
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 1ae2ce2bcc0b3494b00fffa750f3ca46d26fe08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715346"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="315a6-103">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="315a6-103">ServiceToEndpointAssociation</span></span>

<span data-ttu-id="315a6-104">Bir hizmeti uç noktayla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="315a6-104">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315a6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="315a6-105">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="315a6-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="315a6-106">Methods</span></span>  

 <span data-ttu-id="315a6-107">ServiceToEndpointAssociation sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="315a6-107">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="315a6-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="315a6-108">Properties</span></span>  

 <span data-ttu-id="315a6-109">ServiceToEndpointAssociation sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="315a6-109">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="315a6-110">ref</span><span class="sxs-lookup"><span data-stu-id="315a6-110">ref</span></span>  

 <span data-ttu-id="315a6-111">Veri türü: hizmet</span><span class="sxs-lookup"><span data-stu-id="315a6-111">Data type: Service</span></span>  
  
 <span data-ttu-id="315a6-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="315a6-112">Access type: Read-only</span></span>  
<span data-ttu-id="315a6-113">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="315a6-113">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="315a6-114">Uç noktayla ilişkili hizmet.</span><span class="sxs-lookup"><span data-stu-id="315a6-114">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="315a6-115">ref</span><span class="sxs-lookup"><span data-stu-id="315a6-115">ref</span></span>  

 <span data-ttu-id="315a6-116">Veri türü: uç nokta</span><span class="sxs-lookup"><span data-stu-id="315a6-116">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="315a6-117">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="315a6-117">Access type: Read-only</span></span>  
<span data-ttu-id="315a6-118">Niteleyiciler: anahtar</span><span class="sxs-lookup"><span data-stu-id="315a6-118">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="315a6-119">Hizmetle ilişkili uç nokta.</span><span class="sxs-lookup"><span data-stu-id="315a6-119">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="315a6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="315a6-120">Requirements</span></span>  
  
|<span data-ttu-id="315a6-121">MOF</span><span class="sxs-lookup"><span data-stu-id="315a6-121">MOF</span></span>|<span data-ttu-id="315a6-122">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="315a6-122">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="315a6-123">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="315a6-123">Namespace</span></span>|<span data-ttu-id="315a6-124">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="315a6-124">Defined in root\ServiceModel</span></span>|
