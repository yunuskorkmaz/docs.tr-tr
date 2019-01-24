---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: e968f5f2d7ffdb193b30762d32a47be3778b98dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621363"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="d91cc-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d91cc-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="d91cc-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d91cc-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d91cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d91cc-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d91cc-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d91cc-105">Methods</span></span>  
 <span data-ttu-id="d91cc-106">AsymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d91cc-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d91cc-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d91cc-107">Properties</span></span>  
 <span data-ttu-id="d91cc-108">AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d91cc-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="d91cc-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="d91cc-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="d91cc-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d91cc-110">Data type: string</span></span>  
  
 <span data-ttu-id="d91cc-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d91cc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91cc-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="d91cc-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="d91cc-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="d91cc-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="d91cc-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d91cc-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d91cc-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d91cc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d91cc-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="d91cc-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d91cc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d91cc-117">Requirements</span></span>  
  
|<span data-ttu-id="d91cc-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d91cc-118">MOF</span></span>|<span data-ttu-id="d91cc-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d91cc-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d91cc-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d91cc-120">Namespace</span></span>|<span data-ttu-id="d91cc-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d91cc-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d91cc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d91cc-122">See also</span></span>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
