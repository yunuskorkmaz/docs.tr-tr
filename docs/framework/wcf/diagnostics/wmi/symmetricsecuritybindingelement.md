---
description: 'Şu konuda daha fazla bilgi edinin: SymmetricSecurityBindingElement'
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c158f0bedec91a74b305f359889dd307cff48079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715307"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="1fce1-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1fce1-103">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="1fce1-104">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1fce1-104">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fce1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1fce1-105">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1fce1-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1fce1-106">Methods</span></span>  

 <span data-ttu-id="1fce1-107">SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1fce1-107">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1fce1-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1fce1-108">Properties</span></span>  

 <span data-ttu-id="1fce1-109">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1fce1-109">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="1fce1-110">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="1fce1-110">MessageProtectionOrder</span></span>  

 <span data-ttu-id="1fce1-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1fce1-111">Data type: string</span></span>  
  
 <span data-ttu-id="1fce1-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1fce1-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1fce1-113">Bu bağlama için ileti şifreleme ve imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="1fce1-113">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="1fce1-114">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="1fce1-114">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="1fce1-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1fce1-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="1fce1-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1fce1-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1fce1-117">Bağlamanın imza onayını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fce1-117">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fce1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fce1-118">Requirements</span></span>  
  
|<span data-ttu-id="1fce1-119">MOF</span><span class="sxs-lookup"><span data-stu-id="1fce1-119">MOF</span></span>|<span data-ttu-id="1fce1-120">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1fce1-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1fce1-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1fce1-121">Namespace</span></span>|<span data-ttu-id="1fce1-122">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="1fce1-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fce1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fce1-123">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
