---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 0f86fc1b410753b5ec100f0a7d43de9badd1401b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196053"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="ce5e8-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ce5e8-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="ce5e8-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ce5e8-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce5e8-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ce5e8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ce5e8-105">Methods</span></span>  
 <span data-ttu-id="ce5e8-106">AsymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ce5e8-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ce5e8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ce5e8-107">Properties</span></span>  
 <span data-ttu-id="ce5e8-108">AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ce5e8-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="ce5e8-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="ce5e8-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="ce5e8-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ce5e8-110">Data type: string</span></span>  
  
 <span data-ttu-id="ce5e8-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ce5e8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce5e8-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="ce5e8-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="ce5e8-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="ce5e8-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="ce5e8-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ce5e8-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ce5e8-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ce5e8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce5e8-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="ce5e8-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce5e8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce5e8-117">Requirements</span></span>  
  
|<span data-ttu-id="ce5e8-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ce5e8-118">MOF</span></span>|<span data-ttu-id="ce5e8-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ce5e8-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ce5e8-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ce5e8-120">Namespace</span></span>|<span data-ttu-id="ce5e8-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ce5e8-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce5e8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5e8-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
