---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 9da8f77ee8ea5dc8b22ac5c0cb5113e906c5dc78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262274"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="92721-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="92721-102">ServiceSecurityAuditBehavior</span></span>

<span data-ttu-id="92721-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="92721-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92721-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="92721-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="92721-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="92721-105">Methods</span></span>  

 <span data-ttu-id="92721-106">ServiceSecurityAuditBehavior sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="92721-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="92721-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="92721-107">Properties</span></span>  

 <span data-ttu-id="92721-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="92721-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="92721-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="92721-109">AuditLogLocation</span></span>  

 <span data-ttu-id="92721-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="92721-110">Data type: string</span></span>  
  
 <span data-ttu-id="92721-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="92721-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92721-112">Denetim günlüğünün konumu.</span><span class="sxs-lookup"><span data-stu-id="92721-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="92721-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="92721-113">MessageAuthenticationAuditLevel</span></span>  

 <span data-ttu-id="92721-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="92721-114">Data type: string</span></span>  
  
 <span data-ttu-id="92721-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="92721-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92721-116">Denetim olaylarını günlüğe kaydetmek için kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="92721-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="92721-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="92721-117">ServiceAuthorizationAuditLevel</span></span>  

 <span data-ttu-id="92721-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="92721-118">Data type: string</span></span>  
  
 <span data-ttu-id="92721-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="92721-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92721-120">Denetim günlüğüne kaydedilen yetkilendirme olaylarının türleri.</span><span class="sxs-lookup"><span data-stu-id="92721-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="92721-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="92721-121">SuppressAuditFailure</span></span>  

 <span data-ttu-id="92721-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="92721-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="92721-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="92721-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92721-124">Denetim günlüğüne yazma başarısızlıklarını gizleme davranışını belirleyen bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="92721-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92721-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92721-125">Requirements</span></span>  
  
|<span data-ttu-id="92721-126">MOF</span><span class="sxs-lookup"><span data-stu-id="92721-126">MOF</span></span>|<span data-ttu-id="92721-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="92721-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="92721-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="92721-128">Namespace</span></span>|<span data-ttu-id="92721-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="92721-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92721-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92721-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
