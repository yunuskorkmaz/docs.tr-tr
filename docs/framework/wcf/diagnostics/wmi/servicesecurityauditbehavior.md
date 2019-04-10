---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203515"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="5b6fb-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="5b6fb-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="5b6fb-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="5b6fb-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b6fb-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5b6fb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5b6fb-105">Methods</span></span>  
 <span data-ttu-id="5b6fb-106">ServiceSecurityAuditBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5b6fb-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5b6fb-107">Properties</span></span>  
 <span data-ttu-id="5b6fb-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5b6fb-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="5b6fb-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="5b6fb-109">AuditLogLocation</span></span>  
 <span data-ttu-id="5b6fb-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5b6fb-110">Data type: string</span></span>  
  
 <span data-ttu-id="5b6fb-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5b6fb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b6fb-112">Denetim günlük dosyasının konumu.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="5b6fb-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="5b6fb-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="5b6fb-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5b6fb-114">Data type: string</span></span>  
  
 <span data-ttu-id="5b6fb-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5b6fb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b6fb-116">Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="5b6fb-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="5b6fb-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="5b6fb-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5b6fb-118">Data type: string</span></span>  
  
 <span data-ttu-id="5b6fb-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5b6fb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b6fb-120">Denetim günlüğüne kaydedilen yetkilendirme olay türlerini.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="5b6fb-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="5b6fb-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="5b6fb-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="5b6fb-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="5b6fb-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5b6fb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5b6fb-124">Denetim günlüğüne yazma başarısızlıklarını gösterme/gizleme davranışını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b6fb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b6fb-125">Requirements</span></span>  
  
|<span data-ttu-id="5b6fb-126">MOF</span><span class="sxs-lookup"><span data-stu-id="5b6fb-126">MOF</span></span>|<span data-ttu-id="5b6fb-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5b6fb-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5b6fb-128">Namespace</span></span>|<span data-ttu-id="5b6fb-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5b6fb-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b6fb-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b6fb-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
