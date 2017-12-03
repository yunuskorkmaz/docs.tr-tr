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
ms.openlocfilehash: 5c829f68fe994b47fe880febb4d3ac2020fde2d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="cf61e-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="cf61e-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="cf61e-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="cf61e-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf61e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf61e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="cf61e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf61e-105">Methods</span></span>  
 <span data-ttu-id="cf61e-106">ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cf61e-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cf61e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cf61e-107">Properties</span></span>  
 <span data-ttu-id="cf61e-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cf61e-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="cf61e-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="cf61e-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="cf61e-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cf61e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="cf61e-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf61e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf61e-112">Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cf61e-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="cf61e-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="cf61e-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="cf61e-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cf61e-114">Data type: string</span></span>  
  
 <span data-ttu-id="cf61e-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf61e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf61e-116">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf61e-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="cf61e-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="cf61e-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="cf61e-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cf61e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cf61e-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf61e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf61e-120">Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cf61e-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="cf61e-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="cf61e-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="cf61e-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cf61e-122">Data type: string</span></span>  
  
 <span data-ttu-id="cf61e-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf61e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf61e-124">WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf61e-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="cf61e-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="cf61e-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="cf61e-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cf61e-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="cf61e-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cf61e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cf61e-128">Hata ayıklama amacıyla istemcilere döndürülen SOAP hatalarının ayrıntılı yönetilen özel durum bilgileri dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf61e-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf61e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf61e-129">Requirements</span></span>  
  
|<span data-ttu-id="cf61e-130">MOF</span><span class="sxs-lookup"><span data-stu-id="cf61e-130">MOF</span></span>|<span data-ttu-id="cf61e-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cf61e-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cf61e-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cf61e-132">Namespace</span></span>|<span data-ttu-id="cf61e-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cf61e-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf61e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf61e-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
