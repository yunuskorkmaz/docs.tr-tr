---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485901"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="701c6-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="701c6-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="701c6-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="701c6-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="701c6-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="701c6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="701c6-105">Methods</span></span>  
 <span data-ttu-id="701c6-106">ServiceSecurityAuditBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="701c6-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="701c6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="701c6-107">Properties</span></span>  
 <span data-ttu-id="701c6-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="701c6-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="701c6-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="701c6-109">AuditLogLocation</span></span>  
 <span data-ttu-id="701c6-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="701c6-110">Data type: string</span></span>  
  
 <span data-ttu-id="701c6-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="701c6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701c6-112">Denetim günlüğü konumu.</span><span class="sxs-lookup"><span data-stu-id="701c6-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="701c6-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="701c6-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="701c6-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="701c6-114">Data type: string</span></span>  
  
 <span data-ttu-id="701c6-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="701c6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701c6-116">Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="701c6-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="701c6-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="701c6-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="701c6-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="701c6-118">Data type: string</span></span>  
  
 <span data-ttu-id="701c6-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="701c6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701c6-120">Denetim günlüğüne yetkilendirme olay türleri.</span><span class="sxs-lookup"><span data-stu-id="701c6-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="701c6-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="701c6-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="701c6-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="701c6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="701c6-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="701c6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701c6-124">Denetim günlüğü yazma hataları gizleme için davranışını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="701c6-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701c6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="701c6-125">Requirements</span></span>  
  
|<span data-ttu-id="701c6-126">MOF</span><span class="sxs-lookup"><span data-stu-id="701c6-126">MOF</span></span>|<span data-ttu-id="701c6-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="701c6-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="701c6-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="701c6-128">Namespace</span></span>|<span data-ttu-id="701c6-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="701c6-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="701c6-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="701c6-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
