---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af2dbd9e06876622b57379e17dbb4503cddbaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="d3fdd-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="d3fdd-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="d3fdd-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="d3fdd-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3fdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3fdd-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d3fdd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3fdd-105">Methods</span></span>  
 <span data-ttu-id="d3fdd-106">ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d3fdd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d3fdd-107">Properties</span></span>  
 <span data-ttu-id="d3fdd-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d3fdd-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="d3fdd-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="d3fdd-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="d3fdd-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d3fdd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d3fdd-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d3fdd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3fdd-112">Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="d3fdd-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="d3fdd-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="d3fdd-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d3fdd-114">Data type: string</span></span>  
  
 <span data-ttu-id="d3fdd-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d3fdd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3fdd-116">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="d3fdd-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="d3fdd-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="d3fdd-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d3fdd-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d3fdd-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d3fdd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3fdd-120">Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="d3fdd-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="d3fdd-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="d3fdd-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d3fdd-122">Data type: string</span></span>  
  
 <span data-ttu-id="d3fdd-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d3fdd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3fdd-124">WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="d3fdd-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="d3fdd-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="d3fdd-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d3fdd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d3fdd-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d3fdd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3fdd-128">Hata ayıklama amacıyla istemcilere döndürülen SOAP hatalarının ayrıntılı yönetilen özel durum bilgileri dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3fdd-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3fdd-129">Requirements</span></span>  
  
|<span data-ttu-id="d3fdd-130">MOF</span><span class="sxs-lookup"><span data-stu-id="d3fdd-130">MOF</span></span>|<span data-ttu-id="d3fdd-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d3fdd-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d3fdd-132">Namespace</span></span>|<span data-ttu-id="d3fdd-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d3fdd-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3fdd-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3fdd-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
