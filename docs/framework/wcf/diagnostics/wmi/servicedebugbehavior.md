---
description: 'Şu konuda daha fazla bilgi edinin: ServiceDebugBehavior'
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 3b384c209524267c72a12d96bc845b694144ba19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715541"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="f36d9-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="f36d9-103">ServiceDebugBehavior</span></span>

<span data-ttu-id="f36d9-104">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="f36d9-104">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f36d9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f36d9-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f36d9-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f36d9-106">Methods</span></span>  

 <span data-ttu-id="f36d9-107">ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f36d9-107">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f36d9-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f36d9-108">Properties</span></span>  

 <span data-ttu-id="f36d9-109">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f36d9-109">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="f36d9-110">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="f36d9-110">HttpHelpPageEnabled</span></span>  

 <span data-ttu-id="f36d9-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f36d9-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="f36d9-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f36d9-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f36d9-113">Hizmetin WSDL 'sini öznitelik tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="f36d9-113">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="f36d9-114">'Nin HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="f36d9-114">HttpHelpPageUrl</span></span>  

 <span data-ttu-id="f36d9-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f36d9-115">Data type: string</span></span>  
  
 <span data-ttu-id="f36d9-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f36d9-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f36d9-117">Hizmet WSDL 'sinin HTTP kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f36d9-117">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="f36d9-118">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="f36d9-118">HttpsHelpPageEnabled</span></span>  

 <span data-ttu-id="f36d9-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f36d9-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="f36d9-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f36d9-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f36d9-121">Hizmetin WSDL 'nin HTTPS üzerinden özniteliği tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpsGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="f36d9-121">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="f36d9-122">'Nin HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="f36d9-122">HttpsHelpPageUrl</span></span>  

 <span data-ttu-id="f36d9-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f36d9-123">Data type: string</span></span>  
  
 <span data-ttu-id="f36d9-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f36d9-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f36d9-125">Hizmet WSDL 'sinin HTTPS kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f36d9-125">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="f36d9-126">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="f36d9-126">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="f36d9-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f36d9-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="f36d9-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f36d9-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f36d9-129">Yönetilen özel durum bilgilerinin, istemcilere hata ayıklama amacıyla döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f36d9-129">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f36d9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f36d9-130">Requirements</span></span>  
  
|<span data-ttu-id="f36d9-131">MOF</span><span class="sxs-lookup"><span data-stu-id="f36d9-131">MOF</span></span>|<span data-ttu-id="f36d9-132">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f36d9-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f36d9-133">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f36d9-133">Namespace</span></span>|<span data-ttu-id="f36d9-134">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="f36d9-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f36d9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f36d9-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
