---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="b505e-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="b505e-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="b505e-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="b505e-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b505e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b505e-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b505e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b505e-105">Methods</span></span>  
 <span data-ttu-id="b505e-106">ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="b505e-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b505e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b505e-107">Properties</span></span>  
 <span data-ttu-id="b505e-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b505e-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="b505e-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="b505e-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="b505e-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b505e-110">Data type: string</span></span>  
  
 <span data-ttu-id="b505e-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b505e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b505e-112">Hizmet meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b505e-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="b505e-113">De</span><span class="sxs-lookup"><span data-stu-id="b505e-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="b505e-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="b505e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b505e-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b505e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b505e-116">Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b505e-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="b505e-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="b505e-117">HttpGetUrl</span></span>  
 <span data-ttu-id="b505e-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b505e-118">Data type: string</span></span>  
  
 <span data-ttu-id="b505e-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b505e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b505e-120">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b505e-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="b505e-121">De</span><span class="sxs-lookup"><span data-stu-id="b505e-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="b505e-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="b505e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b505e-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b505e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b505e-124">Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b505e-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="b505e-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="b505e-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="b505e-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b505e-126">Data type: string</span></span>  
  
 <span data-ttu-id="b505e-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b505e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b505e-128">WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b505e-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b505e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b505e-129">Requirements</span></span>  
  
|<span data-ttu-id="b505e-130">MOF</span><span class="sxs-lookup"><span data-stu-id="b505e-130">MOF</span></span>|<span data-ttu-id="b505e-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b505e-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b505e-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b505e-132">Namespace</span></span>|<span data-ttu-id="b505e-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b505e-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b505e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b505e-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
