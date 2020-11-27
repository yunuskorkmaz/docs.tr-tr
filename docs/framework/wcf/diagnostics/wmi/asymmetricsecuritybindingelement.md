---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 00485ff80a0064e700d99203de3aa581d3761f30
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255734"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="2b1a4-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2b1a4-102">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="2b1a4-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2b1a4-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1a4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b1a4-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2b1a4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2b1a4-105">Methods</span></span>  

 <span data-ttu-id="2b1a4-106">AsymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="2b1a4-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2b1a4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2b1a4-107">Properties</span></span>  

 <span data-ttu-id="2b1a4-108">AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2b1a4-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="2b1a4-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="2b1a4-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="2b1a4-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2b1a4-110">Data type: string</span></span>  
  
 <span data-ttu-id="2b1a4-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2b1a4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b1a4-112">Bu bağlama için ileti şifreleme ve imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="2b1a4-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="2b1a4-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="2b1a4-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="2b1a4-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2b1a4-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="2b1a4-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2b1a4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2b1a4-116">Bağlamanın imza onayını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b1a4-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b1a4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b1a4-117">Requirements</span></span>  
  
|<span data-ttu-id="2b1a4-118">MOF</span><span class="sxs-lookup"><span data-stu-id="2b1a4-118">MOF</span></span>|<span data-ttu-id="2b1a4-119">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b1a4-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2b1a4-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2b1a4-120">Namespace</span></span>|<span data-ttu-id="2b1a4-121">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="2b1a4-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b1a4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b1a4-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
