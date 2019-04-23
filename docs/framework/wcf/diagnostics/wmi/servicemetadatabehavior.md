---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976145"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="992f6-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="992f6-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="992f6-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="992f6-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="992f6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="992f6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="992f6-105">Methods</span></span>  
 <span data-ttu-id="992f6-106">ServiceMetadataBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="992f6-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="992f6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="992f6-107">Properties</span></span>  
 <span data-ttu-id="992f6-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="992f6-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="992f6-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="992f6-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="992f6-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="992f6-110">Data type: string</span></span>  
  
 <span data-ttu-id="992f6-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="992f6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="992f6-112">Hizmet meta veri isteği yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="992f6-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="992f6-113">De</span><span class="sxs-lookup"><span data-stu-id="992f6-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="992f6-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="992f6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="992f6-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="992f6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="992f6-116">Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="992f6-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="992f6-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="992f6-117">HttpGetUrl</span></span>  
 <span data-ttu-id="992f6-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="992f6-118">Data type: string</span></span>  
  
 <span data-ttu-id="992f6-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="992f6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="992f6-120">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="992f6-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="992f6-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="992f6-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="992f6-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="992f6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="992f6-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="992f6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="992f6-124">Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="992f6-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="992f6-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="992f6-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="992f6-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="992f6-126">Data type: string</span></span>  
  
 <span data-ttu-id="992f6-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="992f6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="992f6-128">WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="992f6-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="992f6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="992f6-129">Requirements</span></span>  
  
|<span data-ttu-id="992f6-130">MOF</span><span class="sxs-lookup"><span data-stu-id="992f6-130">MOF</span></span>|<span data-ttu-id="992f6-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="992f6-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="992f6-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="992f6-132">Namespace</span></span>|<span data-ttu-id="992f6-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="992f6-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="992f6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="992f6-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
