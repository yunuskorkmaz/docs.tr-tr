---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: f5592e0fd02d34b2882182196e0aa9425672a8fe
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838305"
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="14f9b-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="14f9b-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="14f9b-103">Yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="14f9b-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="14f9b-104">Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` öğesidir "Varsayılan" veya "Öbekli".</span><span class="sxs-lookup"><span data-stu-id="14f9b-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="14f9b-105">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="14f9b-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="14f9b-106">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="14f9b-106">\<federationConfiguration></span></span>  
<span data-ttu-id="14f9b-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="14f9b-107">\<cookieHandler></span></span>  
<span data-ttu-id="14f9b-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="14f9b-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f9b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14f9b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14f9b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14f9b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14f9b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14f9b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14f9b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14f9b-112">Attributes</span></span>  
  
|<span data-ttu-id="14f9b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14f9b-113">Attribute</span></span>|<span data-ttu-id="14f9b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14f9b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14f9b-115">Öbek boyutu</span><span class="sxs-lookup"><span data-stu-id="14f9b-115">chunkSize</span></span>|<span data-ttu-id="14f9b-116">Herhangi bir HTTP tanımlama bilgisi için HTTP tanımlama bilgisi verisi karakterlerinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="14f9b-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="14f9b-117">Öbek boyutu ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14f9b-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="14f9b-118">Web tarayıcısı tanımlama bilgilerini ve etki alanı başına izin verilen sayıyı boyutuna farklı sınırlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="14f9b-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="14f9b-119">Örneğin, özgün Netscape belirtimi limitler hükümeti: 300 tanımlama bilgilerini toplam tanımlama bilgisi üstbilgisi (meta veriler, yalnızca tanımlama bilgisi değeri dahil) başına 4096 bayt ve etki alanı başına 20 tanımlama bilgileri.</span><span class="sxs-lookup"><span data-stu-id="14f9b-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="14f9b-120">Varsayılan değer 2000'dir.</span><span class="sxs-lookup"><span data-stu-id="14f9b-120">The default is 2000.</span></span> <span data-ttu-id="14f9b-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="14f9b-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14f9b-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14f9b-122">Child Elements</span></span>  
 <span data-ttu-id="14f9b-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="14f9b-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14f9b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14f9b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="14f9b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="14f9b-125">Element</span></span>|<span data-ttu-id="14f9b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14f9b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14f9b-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="14f9b-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="14f9b-128">Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri (SAM) kullanır.</span><span class="sxs-lookup"><span data-stu-id="14f9b-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14f9b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14f9b-129">Remarks</span></span>  
 <span data-ttu-id="14f9b-130">Belirttiğinizde bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> ayarlayarak `mode` özniteliği `<cookieHandler>` "Varsayılan" veya "Öbekli" öğesine, tanımlama bilgisi işleyici okumak ve tanımlama bilgileri dahil ederek yazmak için kullandığı öbek boyutu belirtebilirsiniz bir `<chunkedCookieHandler>` alt öğesi ve ayarı, `chunkSize` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="14f9b-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="14f9b-131">Varsa `<chunkedCookieHandler>` öğesi yoksa, 2000 bayt varsayılan öbek boyutu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14f9b-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="14f9b-132">Bu öğe olamaz belirtilen `mode` özniteliği "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="14f9b-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="14f9b-133">`<chunkedCookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="14f9b-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14f9b-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="14f9b-134">Example</span></span>  
 <span data-ttu-id="14f9b-135">Aşağıdaki örnek, tanımlama bilgilerini yazar 3000 bayt öbekler halinde bir öbekli tanımlama bilgisi işleyicisi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="14f9b-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14f9b-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14f9b-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
