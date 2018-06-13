---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 76c4992c5364ed9800e58d120c099aceedb2799c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485687"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="204dd-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="204dd-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="204dd-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="204dd-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="204dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="204dd-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="204dd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="204dd-105">Methods</span></span>  
 <span data-ttu-id="204dd-106">ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="204dd-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="204dd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="204dd-107">Properties</span></span>  
 <span data-ttu-id="204dd-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="204dd-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="204dd-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="204dd-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="204dd-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="204dd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="204dd-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="204dd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="204dd-112">Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="204dd-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="204dd-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="204dd-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="204dd-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="204dd-114">Data type: string</span></span>  
  
 <span data-ttu-id="204dd-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="204dd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="204dd-116">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="204dd-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="204dd-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="204dd-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="204dd-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="204dd-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="204dd-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="204dd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="204dd-120">Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="204dd-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="204dd-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="204dd-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="204dd-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="204dd-122">Data type: string</span></span>  
  
 <span data-ttu-id="204dd-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="204dd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="204dd-124">WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="204dd-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="204dd-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="204dd-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="204dd-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="204dd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="204dd-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="204dd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="204dd-128">Hata ayıklama amacıyla istemcilere döndürülen SOAP hatalarının ayrıntılı yönetilen özel durum bilgileri dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="204dd-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="204dd-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="204dd-129">Requirements</span></span>  
  
|<span data-ttu-id="204dd-130">MOF</span><span class="sxs-lookup"><span data-stu-id="204dd-130">MOF</span></span>|<span data-ttu-id="204dd-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="204dd-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="204dd-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="204dd-132">Namespace</span></span>|<span data-ttu-id="204dd-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="204dd-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="204dd-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="204dd-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
