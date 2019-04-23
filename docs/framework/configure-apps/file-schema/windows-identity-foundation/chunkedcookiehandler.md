---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: d9c81d5de7bea343f0d67fa00037763fbae7b8c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120789"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="4379e-101">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="4379e-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="4379e-102">Yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="4379e-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="4379e-103">Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` öğesidir "Varsayılan" veya "Öbekli".</span><span class="sxs-lookup"><span data-stu-id="4379e-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="4379e-104">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="4379e-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="4379e-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="4379e-105">\<federationConfiguration></span></span>  
<span data-ttu-id="4379e-106">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="4379e-106">\<cookieHandler></span></span>  
<span data-ttu-id="4379e-107">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="4379e-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4379e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4379e-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4379e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4379e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4379e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4379e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4379e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4379e-111">Attributes</span></span>  
  
|<span data-ttu-id="4379e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4379e-112">Attribute</span></span>|<span data-ttu-id="4379e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4379e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4379e-114">Öbek boyutu</span><span class="sxs-lookup"><span data-stu-id="4379e-114">chunkSize</span></span>|<span data-ttu-id="4379e-115">Herhangi bir HTTP tanımlama bilgisi için HTTP tanımlama bilgisi verisi karakterlerinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="4379e-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="4379e-116">Öbek boyutu ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4379e-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="4379e-117">Web tarayıcısı tanımlama bilgilerini ve etki alanı başına izin verilen sayıyı boyutuna farklı sınırlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4379e-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="4379e-118">Örneğin, özgün Netscape belirtimi limitler hükümeti: 300 tanımlama bilgilerini (meta veriler, yalnızca tanımlama bilgisi değeri dahil) tanımlama bilgisi üstbilgisi başına 4096 bayt ve etki alanı başına 20 tanımlama bilgisi toplam.</span><span class="sxs-lookup"><span data-stu-id="4379e-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="4379e-119">Varsayılan değer 2000'dir.</span><span class="sxs-lookup"><span data-stu-id="4379e-119">The default is 2000.</span></span> <span data-ttu-id="4379e-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4379e-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4379e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4379e-121">Child Elements</span></span>  
 <span data-ttu-id="4379e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4379e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4379e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4379e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4379e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4379e-124">Element</span></span>|<span data-ttu-id="4379e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4379e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4379e-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="4379e-126">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="4379e-127">Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri (SAM) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4379e-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4379e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4379e-128">Remarks</span></span>  
 <span data-ttu-id="4379e-129">Belirttiğinizde bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> ayarlayarak `mode` özniteliği `<cookieHandler>` "Varsayılan" veya "Öbekli" öğesine, tanımlama bilgisi işleyici okumak ve tanımlama bilgileri dahil ederek yazmak için kullandığı öbek boyutu belirtebilirsiniz bir `<chunkedCookieHandler>` alt öğesi ve ayarı, `chunkSize` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4379e-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="4379e-130">Varsa `<chunkedCookieHandler>` öğesi yoksa, 2000 bayt varsayılan öbek boyutu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4379e-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="4379e-131">Bu öğe olamaz belirtilen `mode` özniteliği "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4379e-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="4379e-132">`<chunkedCookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4379e-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4379e-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="4379e-133">Example</span></span>  
 <span data-ttu-id="4379e-134">Aşağıdaki örnek, tanımlama bilgilerini yazar 3000 bayt öbekler halinde bir öbekli tanımlama bilgisi işleyicisi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4379e-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4379e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4379e-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
