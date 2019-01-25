---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: d6f0e4741aa10bff450a29cfd7a9e63e226c6495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498888"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="1f976-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="1f976-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="1f976-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="1f976-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f976-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f976-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1f976-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1f976-105">Methods</span></span>  
 <span data-ttu-id="1f976-106">ServiceDebugBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1f976-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1f976-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1f976-107">Properties</span></span>  
 <span data-ttu-id="1f976-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1f976-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="1f976-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="1f976-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="1f976-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1f976-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f976-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1f976-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f976-112">Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1f976-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="1f976-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="1f976-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="1f976-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1f976-114">Data type: string</span></span>  
  
 <span data-ttu-id="1f976-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1f976-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f976-116">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1f976-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="1f976-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="1f976-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="1f976-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1f976-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f976-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1f976-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f976-120">Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1f976-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="1f976-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="1f976-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="1f976-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1f976-122">Data type: string</span></span>  
  
 <span data-ttu-id="1f976-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1f976-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f976-124">WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1f976-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="1f976-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="1f976-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="1f976-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1f976-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f976-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1f976-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f976-128">Hata ayıklama amacıyla, istemcilere dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f976-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f976-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f976-129">Requirements</span></span>  
  
|<span data-ttu-id="1f976-130">MOF</span><span class="sxs-lookup"><span data-stu-id="1f976-130">MOF</span></span>|<span data-ttu-id="1f976-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1f976-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1f976-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1f976-132">Namespace</span></span>|<span data-ttu-id="1f976-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f976-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f976-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f976-134">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
