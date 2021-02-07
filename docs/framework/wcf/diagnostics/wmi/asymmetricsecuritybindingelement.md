---
description: 'Daha fazla bilgi edinin: AsymmetricSecurityBindingElement'
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 25d0ac205491e9ce27c59d3a0670d1e4a3150e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757949"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="e8858-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e8858-103">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="e8858-104">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e8858-104">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8858-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8858-105">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e8858-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e8858-106">Methods</span></span>  

 <span data-ttu-id="e8858-107">AsymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e8858-107">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e8858-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e8858-108">Properties</span></span>  

 <span data-ttu-id="e8858-109">AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e8858-109">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e8858-110">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e8858-110">MessageProtectionOrder</span></span>  

 <span data-ttu-id="e8858-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e8858-111">Data type: string</span></span>  
  
 <span data-ttu-id="e8858-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e8858-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e8858-113">Bu bağlama için ileti şifreleme ve imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="e8858-113">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e8858-114">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e8858-114">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="e8858-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e8858-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="e8858-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e8858-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e8858-117">Bağlamanın imza onayını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8858-117">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8858-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8858-118">Requirements</span></span>  
  
|<span data-ttu-id="e8858-119">MOF</span><span class="sxs-lookup"><span data-stu-id="e8858-119">MOF</span></span>|<span data-ttu-id="e8858-120">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e8858-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e8858-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e8858-121">Namespace</span></span>|<span data-ttu-id="e8858-122">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="e8858-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8858-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8858-123">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
