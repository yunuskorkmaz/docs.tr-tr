---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: dba4abd74cdddeb2b641feec5902413fe0704b1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262300"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="52c24-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="52c24-102">ServiceDebugBehavior</span></span>

<span data-ttu-id="52c24-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="52c24-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c24-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="52c24-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="52c24-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="52c24-105">Methods</span></span>  

 <span data-ttu-id="52c24-106">ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="52c24-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52c24-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="52c24-107">Properties</span></span>  

 <span data-ttu-id="52c24-108">ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="52c24-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="52c24-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="52c24-109">HttpHelpPageEnabled</span></span>  

 <span data-ttu-id="52c24-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="52c24-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="52c24-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="52c24-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c24-112">Hizmetin WSDL 'sini öznitelik tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="52c24-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="52c24-113">'Nin HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="52c24-113">HttpHelpPageUrl</span></span>  

 <span data-ttu-id="52c24-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="52c24-114">Data type: string</span></span>  
  
 <span data-ttu-id="52c24-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="52c24-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c24-116">Hizmet WSDL 'sinin HTTP kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52c24-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="52c24-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="52c24-117">HttpsHelpPageEnabled</span></span>  

 <span data-ttu-id="52c24-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="52c24-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="52c24-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="52c24-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c24-120">Hizmetin WSDL 'nin HTTPS üzerinden özniteliği tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpsGetUrl` .</span><span class="sxs-lookup"><span data-stu-id="52c24-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="52c24-121">'Nin HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="52c24-121">HttpsHelpPageUrl</span></span>  

 <span data-ttu-id="52c24-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="52c24-122">Data type: string</span></span>  
  
 <span data-ttu-id="52c24-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="52c24-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c24-124">Hizmet WSDL 'sinin HTTPS kullanılarak alınması için yayımlandığı konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52c24-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="52c24-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="52c24-125">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="52c24-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="52c24-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="52c24-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="52c24-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52c24-128">Yönetilen özel durum bilgilerinin, istemcilere hata ayıklama amacıyla döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="52c24-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c24-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52c24-129">Requirements</span></span>  
  
|<span data-ttu-id="52c24-130">MOF</span><span class="sxs-lookup"><span data-stu-id="52c24-130">MOF</span></span>|<span data-ttu-id="52c24-131">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="52c24-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52c24-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="52c24-132">Namespace</span></span>|<span data-ttu-id="52c24-133">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="52c24-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52c24-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c24-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
