---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090920"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="dd80c-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="dd80c-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="dd80c-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="dd80c-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd80c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd80c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="dd80c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dd80c-105">Methods</span></span>  
 <span data-ttu-id="dd80c-106">ServiceDebugBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="dd80c-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dd80c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="dd80c-107">Properties</span></span>  
 <span data-ttu-id="dd80c-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dd80c-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="dd80c-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="dd80c-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="dd80c-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="dd80c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="dd80c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dd80c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd80c-112">Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dd80c-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="dd80c-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="dd80c-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="dd80c-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dd80c-114">Data type: string</span></span>  
  
 <span data-ttu-id="dd80c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dd80c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd80c-116">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd80c-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="dd80c-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="dd80c-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="dd80c-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="dd80c-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="dd80c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dd80c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd80c-120">Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dd80c-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="dd80c-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="dd80c-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="dd80c-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dd80c-122">Data type: string</span></span>  
  
 <span data-ttu-id="dd80c-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dd80c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd80c-124">WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd80c-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="dd80c-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="dd80c-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="dd80c-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="dd80c-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="dd80c-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dd80c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dd80c-128">Hata ayıklama amacıyla, istemcilere dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd80c-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd80c-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd80c-129">Requirements</span></span>  
  
|<span data-ttu-id="dd80c-130">MOF</span><span class="sxs-lookup"><span data-stu-id="dd80c-130">MOF</span></span>|<span data-ttu-id="dd80c-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dd80c-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dd80c-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="dd80c-132">Namespace</span></span>|<span data-ttu-id="dd80c-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dd80c-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd80c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd80c-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
