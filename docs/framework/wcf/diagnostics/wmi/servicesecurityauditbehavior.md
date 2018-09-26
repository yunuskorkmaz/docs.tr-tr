---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
ms.openlocfilehash: 8f43ee752830d95db6bbbdbe311b6d77735e31b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196899"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="b3ec2-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="b3ec2-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="b3ec2-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="b3ec2-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ec2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3ec2-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b3ec2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b3ec2-105">Methods</span></span>  
 <span data-ttu-id="b3ec2-106">ServiceSecurityAuditBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b3ec2-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b3ec2-107">Properties</span></span>  
 <span data-ttu-id="b3ec2-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b3ec2-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="b3ec2-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="b3ec2-109">AuditLogLocation</span></span>  
 <span data-ttu-id="b3ec2-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b3ec2-110">Data type: string</span></span>  
  
 <span data-ttu-id="b3ec2-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3ec2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3ec2-112">Denetim günlük dosyasının konumu.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="b3ec2-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="b3ec2-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="b3ec2-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b3ec2-114">Data type: string</span></span>  
  
 <span data-ttu-id="b3ec2-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3ec2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3ec2-116">Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="b3ec2-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="b3ec2-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="b3ec2-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b3ec2-118">Data type: string</span></span>  
  
 <span data-ttu-id="b3ec2-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3ec2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3ec2-120">Denetim günlüğüne kaydedilen yetkilendirme olay türlerini.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="b3ec2-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="b3ec2-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="b3ec2-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b3ec2-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b3ec2-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3ec2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3ec2-124">Denetim günlüğüne yazma başarısızlıklarını gösterme/gizleme davranışını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3ec2-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3ec2-125">Requirements</span></span>  
  
|<span data-ttu-id="b3ec2-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b3ec2-126">MOF</span></span>|<span data-ttu-id="b3ec2-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b3ec2-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b3ec2-128">Namespace</span></span>|<span data-ttu-id="b3ec2-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b3ec2-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3ec2-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3ec2-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
