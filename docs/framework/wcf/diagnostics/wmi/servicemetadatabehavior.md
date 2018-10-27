---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188839"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="67522-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="67522-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="67522-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="67522-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67522-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67522-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="67522-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="67522-105">Methods</span></span>  
 <span data-ttu-id="67522-106">ServiceMetadataBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="67522-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="67522-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="67522-107">Properties</span></span>  
 <span data-ttu-id="67522-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="67522-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="67522-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="67522-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="67522-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="67522-110">Data type: string</span></span>  
  
 <span data-ttu-id="67522-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="67522-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67522-112">Hizmet meta veri isteği yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67522-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="67522-113">De</span><span class="sxs-lookup"><span data-stu-id="67522-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="67522-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="67522-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="67522-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="67522-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67522-116">Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="67522-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="67522-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="67522-117">HttpGetUrl</span></span>  
 <span data-ttu-id="67522-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="67522-118">Data type: string</span></span>  
  
 <span data-ttu-id="67522-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="67522-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67522-120">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67522-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="67522-121">De</span><span class="sxs-lookup"><span data-stu-id="67522-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="67522-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="67522-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="67522-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="67522-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67522-124">Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="67522-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="67522-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="67522-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="67522-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="67522-126">Data type: string</span></span>  
  
 <span data-ttu-id="67522-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="67522-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67522-128">WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67522-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67522-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67522-129">Requirements</span></span>  
  
|<span data-ttu-id="67522-130">MOF</span><span class="sxs-lookup"><span data-stu-id="67522-130">MOF</span></span>|<span data-ttu-id="67522-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="67522-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="67522-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="67522-132">Namespace</span></span>|<span data-ttu-id="67522-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="67522-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67522-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67522-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
