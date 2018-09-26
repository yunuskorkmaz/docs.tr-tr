---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
ms.openlocfilehash: 180b64f6f37e5c765585e52b292319816618be28
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198858"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="09ed1-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="09ed1-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="09ed1-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="09ed1-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ed1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09ed1-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="09ed1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="09ed1-105">Methods</span></span>  
 <span data-ttu-id="09ed1-106">SymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="09ed1-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="09ed1-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="09ed1-107">Properties</span></span>  
 <span data-ttu-id="09ed1-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="09ed1-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="09ed1-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="09ed1-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="09ed1-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09ed1-110">Data type: string</span></span>  
  
 <span data-ttu-id="09ed1-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09ed1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09ed1-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="09ed1-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="09ed1-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="09ed1-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="09ed1-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="09ed1-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="09ed1-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09ed1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09ed1-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="09ed1-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ed1-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09ed1-117">Requirements</span></span>  
  
|<span data-ttu-id="09ed1-118">MOF</span><span class="sxs-lookup"><span data-stu-id="09ed1-118">MOF</span></span>|<span data-ttu-id="09ed1-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="09ed1-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="09ed1-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="09ed1-120">Namespace</span></span>|<span data-ttu-id="09ed1-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="09ed1-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09ed1-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09ed1-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
