---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 193b783e44fe4386d3575e180dc5baa6a7f9a8be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758379"
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="44257-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="44257-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="44257-103">Yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="44257-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="44257-104">Bu öğe yalnızca mevcut olabilir, `mode` özniteliği `<cookieHandler>` öğesidir "Varsayılan" veya "Öbekli".</span><span class="sxs-lookup"><span data-stu-id="44257-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="44257-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="44257-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="44257-106">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="44257-106">\<federationConfiguration></span></span>  
<span data-ttu-id="44257-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="44257-107">\<cookieHandler></span></span>  
<span data-ttu-id="44257-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="44257-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44257-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44257-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44257-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44257-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44257-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44257-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44257-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44257-112">Attributes</span></span>  
  
|<span data-ttu-id="44257-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44257-113">Attribute</span></span>|<span data-ttu-id="44257-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44257-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44257-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="44257-115">chunkSize</span></span>|<span data-ttu-id="44257-116">Karakterleri, herhangi bir HTTP tanımlama bilgisi HTTP tanımlama bilgisi verileri, en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="44257-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="44257-117">Öbek boyutu ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44257-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="44257-118">Web tarayıcıları farklı sınırlara tanımlama bilgileri ve etki alanı başına izin verilen sayıyı boyutuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44257-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="44257-119">Örneğin, özgün Netscape belirtiminin bu sınırları belirlenen: 300 tanımlama bilgilerini toplam, 4096 bayt tanımlama bilgisi üstbilgisi (meta verileri, yalnızca tanımlama bilgisi değeri dahil) ve etki alanı başına 20 tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="44257-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="44257-120">Varsayılan değer 2000'dir.</span><span class="sxs-lookup"><span data-stu-id="44257-120">The default is 2000.</span></span> <span data-ttu-id="44257-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="44257-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44257-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44257-122">Child Elements</span></span>  
 <span data-ttu-id="44257-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="44257-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44257-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44257-124">Parent Elements</span></span>  
  
|<span data-ttu-id="44257-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="44257-125">Element</span></span>|<span data-ttu-id="44257-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44257-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44257-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="44257-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="44257-128">Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) okuma ve yazma tanımlama için kullanır.</span><span class="sxs-lookup"><span data-stu-id="44257-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44257-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44257-129">Remarks</span></span>  
 <span data-ttu-id="44257-130">Belirttiğinizde bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> ayarlayarak `mode` özniteliği `<cookieHandler>` "Varsayılan" veya "Chunked" öğesine, tanımlama bilgisi işleyici okumak ve tanımlama bilgileri dahil ederek yazmak için kullandığı öbek boyutu belirtebilirsiniz bir `<chunkedCookieHandler>` alt öğesi ve ayarlama, `chunkSize` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="44257-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="44257-131">Varsa `<chunkedCookieHandler>` öğesi mevcut değil, 2000 bayt varsayılan öbek boyutu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44257-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="44257-132">Bu öğe olamaz belirtilen `mode` özniteliği "Özel" olarak ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="44257-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="44257-133">`<chunkedCookieHandler>` Öğesi ile temsil edilir <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44257-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44257-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="44257-134">Example</span></span>  
 <span data-ttu-id="44257-135">Aşağıdaki örnek 3000 bayt yığınlar halinde tanımlama bilgilerini yazar parçalı tanımlama bilgileri işleyici yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="44257-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44257-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44257-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
