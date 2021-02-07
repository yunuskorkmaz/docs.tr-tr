---
description: 'Daha fazla bilgi edinin: ServiceMetadataBehavior'
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1b1438013ec667b10b300d898687abf6f33f96fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715489"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="0466e-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="0466e-103">ServiceMetadataBehavior</span></span>

<span data-ttu-id="0466e-104">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="0466e-104">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0466e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0466e-105">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0466e-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0466e-106">Methods</span></span>  

 <span data-ttu-id="0466e-107">ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="0466e-107">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0466e-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0466e-108">Properties</span></span>  

 <span data-ttu-id="0466e-109">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0466e-109">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="0466e-110">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="0466e-110">ExternalMetadataLocation</span></span>  

 <span data-ttu-id="0466e-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="0466e-111">Data type: string</span></span>  
  
 <span data-ttu-id="0466e-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0466e-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0466e-113">Hizmetin meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0466e-113">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="0466e-114">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="0466e-114">HttpGetEnabled</span></span>  

 <span data-ttu-id="0466e-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="0466e-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="0466e-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0466e-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0466e-117">Hizmetin WSDL 'sini öznitelik tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="0466e-117">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="0466e-118">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="0466e-118">HttpGetUrl</span></span>  

 <span data-ttu-id="0466e-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="0466e-119">Data type: string</span></span>  
  
 <span data-ttu-id="0466e-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0466e-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0466e-121">Hizmet WSDL 'sinin HTTP kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0466e-121">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="0466e-122">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="0466e-122">HttpsGetEnabled</span></span>  

 <span data-ttu-id="0466e-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="0466e-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="0466e-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0466e-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0466e-125">Hizmetin WSDL 'nin HTTPS üzerinden özniteliği tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpsGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="0466e-125">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="0466e-126">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="0466e-126">HttpsGetUrl</span></span>  

 <span data-ttu-id="0466e-127">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="0466e-127">Data type: string</span></span>  
  
 <span data-ttu-id="0466e-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0466e-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0466e-129">Hizmet WSDL 'sinin HTTPS kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0466e-129">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0466e-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0466e-130">Requirements</span></span>  
  
|<span data-ttu-id="0466e-131">MOF</span><span class="sxs-lookup"><span data-stu-id="0466e-131">MOF</span></span>|<span data-ttu-id="0466e-132">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0466e-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0466e-133">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="0466e-133">Namespace</span></span>|<span data-ttu-id="0466e-134">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="0466e-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0466e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0466e-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
