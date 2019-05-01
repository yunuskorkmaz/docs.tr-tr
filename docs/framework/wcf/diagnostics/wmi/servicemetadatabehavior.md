---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956955"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="d7d8c-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="d7d8c-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="d7d8c-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="d7d8c-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7d8c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d7d8c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d7d8c-105">Methods</span></span>  
 <span data-ttu-id="d7d8c-106">ServiceMetadataBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d7d8c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d7d8c-107">Properties</span></span>  
 <span data-ttu-id="d7d8c-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d7d8c-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="d7d8c-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="d7d8c-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="d7d8c-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7d8c-110">Data type: string</span></span>  
  
 <span data-ttu-id="d7d8c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7d8c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7d8c-112">Hizmet meta veri isteği yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="d7d8c-113">De</span><span class="sxs-lookup"><span data-stu-id="d7d8c-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="d7d8c-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d7d8c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7d8c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7d8c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7d8c-116">Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="d7d8c-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="d7d8c-117">HttpGetUrl</span></span>  
 <span data-ttu-id="d7d8c-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7d8c-118">Data type: string</span></span>  
  
 <span data-ttu-id="d7d8c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7d8c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7d8c-120">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="d7d8c-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="d7d8c-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="d7d8c-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d7d8c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7d8c-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7d8c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7d8c-124">Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="d7d8c-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="d7d8c-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="d7d8c-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7d8c-126">Data type: string</span></span>  
  
 <span data-ttu-id="d7d8c-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7d8c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7d8c-128">WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7d8c-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7d8c-129">Requirements</span></span>  
  
|<span data-ttu-id="d7d8c-130">MOF</span><span class="sxs-lookup"><span data-stu-id="d7d8c-130">MOF</span></span>|<span data-ttu-id="d7d8c-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d7d8c-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d7d8c-132">Namespace</span></span>|<span data-ttu-id="d7d8c-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d7d8c-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7d8c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7d8c-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
