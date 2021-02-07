---
description: 'Hakkında daha fazla bilgi edinin: ServiceSecurityAuditBehavior'
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 5dfb3a70a80d5dea1ed360dcaf3a0db989bf671b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715476"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="82e6d-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="82e6d-103">ServiceSecurityAuditBehavior</span></span>

<span data-ttu-id="82e6d-104">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="82e6d-104">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e6d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="82e6d-105">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="82e6d-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="82e6d-106">Methods</span></span>  

 <span data-ttu-id="82e6d-107">ServiceSecurityAuditBehavior sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="82e6d-107">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="82e6d-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="82e6d-108">Properties</span></span>  

 <span data-ttu-id="82e6d-109">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="82e6d-109">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="82e6d-110">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="82e6d-110">AuditLogLocation</span></span>  

 <span data-ttu-id="82e6d-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="82e6d-111">Data type: string</span></span>  
  
 <span data-ttu-id="82e6d-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="82e6d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82e6d-113">Denetim günlüğünün konumu.</span><span class="sxs-lookup"><span data-stu-id="82e6d-113">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="82e6d-114">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="82e6d-114">MessageAuthenticationAuditLevel</span></span>  

 <span data-ttu-id="82e6d-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="82e6d-115">Data type: string</span></span>  
  
 <span data-ttu-id="82e6d-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="82e6d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82e6d-117">Denetim olaylarını günlüğe kaydetmek için kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="82e6d-117">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="82e6d-118">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="82e6d-118">ServiceAuthorizationAuditLevel</span></span>  

 <span data-ttu-id="82e6d-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="82e6d-119">Data type: string</span></span>  
  
 <span data-ttu-id="82e6d-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="82e6d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82e6d-121">Denetim günlüğüne kaydedilen yetkilendirme olaylarının türleri.</span><span class="sxs-lookup"><span data-stu-id="82e6d-121">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="82e6d-122">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="82e6d-122">SuppressAuditFailure</span></span>  

 <span data-ttu-id="82e6d-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="82e6d-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="82e6d-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="82e6d-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82e6d-125">Denetim günlüğüne yazma başarısızlıklarını gizleme davranışını belirleyen bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="82e6d-125">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e6d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82e6d-126">Requirements</span></span>  
  
|<span data-ttu-id="82e6d-127">MOF</span><span class="sxs-lookup"><span data-stu-id="82e6d-127">MOF</span></span>|<span data-ttu-id="82e6d-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82e6d-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="82e6d-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="82e6d-129">Namespace</span></span>|<span data-ttu-id="82e6d-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="82e6d-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82e6d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e6d-131">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
