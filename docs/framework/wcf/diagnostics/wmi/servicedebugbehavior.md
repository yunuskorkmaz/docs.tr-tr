---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 68b2350f257bc95d8e17f4b9049d67c7f67becae
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452868"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="a360a-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="a360a-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="a360a-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="a360a-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a360a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a360a-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a360a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a360a-105">Methods</span></span>  
 <span data-ttu-id="a360a-106">ServiceDebugBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a360a-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a360a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a360a-107">Properties</span></span>  
 <span data-ttu-id="a360a-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a360a-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="a360a-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="a360a-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="a360a-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="a360a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a360a-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a360a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a360a-112">Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a360a-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="a360a-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="a360a-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="a360a-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a360a-114">Data type: string</span></span>  
  
 <span data-ttu-id="a360a-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a360a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a360a-116">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a360a-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="a360a-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="a360a-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="a360a-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="a360a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a360a-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a360a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a360a-120">Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a360a-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="a360a-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="a360a-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="a360a-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a360a-122">Data type: string</span></span>  
  
 <span data-ttu-id="a360a-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a360a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a360a-124">WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a360a-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="a360a-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="a360a-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="a360a-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="a360a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a360a-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a360a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a360a-128">Hata ayıklama amacıyla, istemcilere dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a360a-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a360a-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a360a-129">Requirements</span></span>  
  
|<span data-ttu-id="a360a-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a360a-130">MOF</span></span>|<span data-ttu-id="a360a-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a360a-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a360a-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a360a-132">Namespace</span></span>|<span data-ttu-id="a360a-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a360a-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a360a-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a360a-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
