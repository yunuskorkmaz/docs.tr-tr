---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: dc48b8742c60714720be3cf4b22ba672f73c720a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570232"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="7f63d-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="7f63d-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="7f63d-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="7f63d-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f63d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f63d-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7f63d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7f63d-105">Methods</span></span>  
 <span data-ttu-id="7f63d-106">ServiceSecurityAuditBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7f63d-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7f63d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7f63d-107">Properties</span></span>  
 <span data-ttu-id="7f63d-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7f63d-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="7f63d-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="7f63d-109">AuditLogLocation</span></span>  
 <span data-ttu-id="7f63d-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7f63d-110">Data type: string</span></span>  
  
 <span data-ttu-id="7f63d-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7f63d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f63d-112">Denetim günlük dosyasının konumu.</span><span class="sxs-lookup"><span data-stu-id="7f63d-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="7f63d-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="7f63d-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="7f63d-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7f63d-114">Data type: string</span></span>  
  
 <span data-ttu-id="7f63d-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7f63d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f63d-116">Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="7f63d-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="7f63d-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="7f63d-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="7f63d-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7f63d-118">Data type: string</span></span>  
  
 <span data-ttu-id="7f63d-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7f63d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f63d-120">Denetim günlüğüne kaydedilen yetkilendirme olay türlerini.</span><span class="sxs-lookup"><span data-stu-id="7f63d-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="7f63d-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="7f63d-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="7f63d-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7f63d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f63d-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7f63d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f63d-124">Denetim günlüğüne yazma başarısızlıklarını gösterme/gizleme davranışını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7f63d-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f63d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f63d-125">Requirements</span></span>  
  
|<span data-ttu-id="7f63d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="7f63d-126">MOF</span></span>|<span data-ttu-id="7f63d-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7f63d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7f63d-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7f63d-128">Namespace</span></span>|<span data-ttu-id="7f63d-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7f63d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f63d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f63d-130">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
