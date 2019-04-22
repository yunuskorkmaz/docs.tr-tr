---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770418"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="15661-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="15661-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="15661-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="15661-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15661-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15661-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="15661-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15661-105">Methods</span></span>  
 <span data-ttu-id="15661-106">SymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="15661-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15661-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="15661-107">Properties</span></span>  
 <span data-ttu-id="15661-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="15661-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="15661-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="15661-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="15661-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="15661-110">Data type: string</span></span>  
  
 <span data-ttu-id="15661-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="15661-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15661-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="15661-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="15661-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="15661-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="15661-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="15661-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="15661-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="15661-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15661-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="15661-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15661-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15661-117">Requirements</span></span>  
  
|<span data-ttu-id="15661-118">MOF</span><span class="sxs-lookup"><span data-stu-id="15661-118">MOF</span></span>|<span data-ttu-id="15661-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="15661-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="15661-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="15661-120">Namespace</span></span>|<span data-ttu-id="15661-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="15661-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15661-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15661-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
