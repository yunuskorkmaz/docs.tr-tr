---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ea9c04c201ff022fcea54b81a998b7020fb2a836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="58786-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="58786-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="58786-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="58786-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58786-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58786-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="58786-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="58786-105">Methods</span></span>  
 <span data-ttu-id="58786-106">ServiceSecurityAuditBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="58786-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="58786-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="58786-107">Properties</span></span>  
 <span data-ttu-id="58786-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="58786-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="58786-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="58786-109">AuditLogLocation</span></span>  
 <span data-ttu-id="58786-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="58786-110">Data type: string</span></span>  
  
 <span data-ttu-id="58786-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58786-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58786-112">Denetim günlüğü konumu.</span><span class="sxs-lookup"><span data-stu-id="58786-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="58786-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="58786-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="58786-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="58786-114">Data type: string</span></span>  
  
 <span data-ttu-id="58786-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58786-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58786-116">Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="58786-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="58786-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="58786-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="58786-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="58786-118">Data type: string</span></span>  
  
 <span data-ttu-id="58786-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58786-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58786-120">Denetim günlüğüne yetkilendirme olay türleri.</span><span class="sxs-lookup"><span data-stu-id="58786-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="58786-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="58786-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="58786-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="58786-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="58786-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58786-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58786-124">Denetim günlüğü yazma hataları gizleme için davranışını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="58786-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58786-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58786-125">Requirements</span></span>  
  
|<span data-ttu-id="58786-126">MOF</span><span class="sxs-lookup"><span data-stu-id="58786-126">MOF</span></span>|<span data-ttu-id="58786-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="58786-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="58786-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="58786-128">Namespace</span></span>|<span data-ttu-id="58786-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="58786-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58786-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58786-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
