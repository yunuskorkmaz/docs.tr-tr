---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 921a880dad0d77558a70dff8a09f75c25a3cbb8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262287"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="24222-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="24222-102">ServiceMetadataBehavior</span></span>

<span data-ttu-id="24222-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="24222-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24222-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="24222-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="24222-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="24222-105">Methods</span></span>  

 <span data-ttu-id="24222-106">ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="24222-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="24222-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="24222-107">Properties</span></span>  

 <span data-ttu-id="24222-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="24222-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="24222-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="24222-109">ExternalMetadataLocation</span></span>  

 <span data-ttu-id="24222-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="24222-110">Data type: string</span></span>  
  
 <span data-ttu-id="24222-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24222-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="24222-112">Hizmetin meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24222-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="24222-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="24222-113">HttpGetEnabled</span></span>  

 <span data-ttu-id="24222-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="24222-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="24222-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24222-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="24222-116">Hizmetin WSDL 'sini öznitelik tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="24222-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="24222-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="24222-117">HttpGetUrl</span></span>  

 <span data-ttu-id="24222-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="24222-118">Data type: string</span></span>  
  
 <span data-ttu-id="24222-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24222-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="24222-120">Hizmet WSDL 'sinin HTTP kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24222-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="24222-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="24222-121">HttpsGetEnabled</span></span>  

 <span data-ttu-id="24222-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="24222-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="24222-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24222-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="24222-124">Hizmetin WSDL 'nin HTTPS üzerinden özniteliği tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpsGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="24222-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="24222-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="24222-125">HttpsGetUrl</span></span>  

 <span data-ttu-id="24222-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="24222-126">Data type: string</span></span>  
  
 <span data-ttu-id="24222-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="24222-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="24222-128">Hizmet WSDL 'sinin HTTPS kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24222-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24222-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24222-129">Requirements</span></span>  
  
|<span data-ttu-id="24222-130">MOF</span><span class="sxs-lookup"><span data-stu-id="24222-130">MOF</span></span>|<span data-ttu-id="24222-131">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="24222-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="24222-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="24222-132">Namespace</span></span>|<span data-ttu-id="24222-133">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="24222-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24222-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24222-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
