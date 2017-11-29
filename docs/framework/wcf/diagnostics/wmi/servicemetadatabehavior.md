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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d10fdd9e33b078fa392e0ef359372913f9ba133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="09b98-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="09b98-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="09b98-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="09b98-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09b98-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="09b98-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="09b98-105">Methods</span></span>  
 <span data-ttu-id="09b98-106">ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="09b98-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="09b98-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="09b98-107">Properties</span></span>  
 <span data-ttu-id="09b98-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="09b98-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="09b98-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="09b98-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="09b98-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09b98-110">Data type: string</span></span>  
  
 <span data-ttu-id="09b98-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09b98-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09b98-112">Hizmet meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="09b98-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="09b98-113">De</span><span class="sxs-lookup"><span data-stu-id="09b98-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="09b98-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="09b98-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="09b98-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09b98-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09b98-116">Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="09b98-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="09b98-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="09b98-117">HttpGetUrl</span></span>  
 <span data-ttu-id="09b98-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09b98-118">Data type: string</span></span>  
  
 <span data-ttu-id="09b98-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09b98-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09b98-120">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="09b98-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="09b98-121">De</span><span class="sxs-lookup"><span data-stu-id="09b98-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="09b98-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="09b98-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="09b98-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09b98-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09b98-124">Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="09b98-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="09b98-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="09b98-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="09b98-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09b98-126">Data type: string</span></span>  
  
 <span data-ttu-id="09b98-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09b98-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09b98-128">WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="09b98-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b98-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09b98-129">Requirements</span></span>  
  
|<span data-ttu-id="09b98-130">MOF</span><span class="sxs-lookup"><span data-stu-id="09b98-130">MOF</span></span>|<span data-ttu-id="09b98-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="09b98-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="09b98-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="09b98-132">Namespace</span></span>|<span data-ttu-id="09b98-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="09b98-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09b98-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09b98-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
