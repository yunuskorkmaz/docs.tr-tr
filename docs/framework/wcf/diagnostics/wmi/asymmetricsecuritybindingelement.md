---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 076313548828f1fbce9c68b48c0fa7db9cca095f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185124"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="14e42-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="14e42-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="14e42-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="14e42-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e42-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14e42-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="14e42-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="14e42-105">Methods</span></span>  
 <span data-ttu-id="14e42-106">AsymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="14e42-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="14e42-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14e42-107">Properties</span></span>  
 <span data-ttu-id="14e42-108">AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="14e42-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="14e42-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="14e42-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="14e42-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14e42-110">Data type: string</span></span>  
  
 <span data-ttu-id="14e42-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14e42-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14e42-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="14e42-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="14e42-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="14e42-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="14e42-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="14e42-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="14e42-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14e42-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14e42-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="14e42-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14e42-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14e42-117">Requirements</span></span>  
  
|<span data-ttu-id="14e42-118">MOF</span><span class="sxs-lookup"><span data-stu-id="14e42-118">MOF</span></span>|<span data-ttu-id="14e42-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="14e42-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="14e42-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="14e42-120">Namespace</span></span>|<span data-ttu-id="14e42-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14e42-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14e42-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14e42-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
