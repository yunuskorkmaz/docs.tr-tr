---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252102"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="7301d-101">\<Öbek için yığın tanımlama ></span><span class="sxs-lookup"><span data-stu-id="7301d-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="7301d-102">Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="7301d-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="7301d-103">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7301d-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
<span data-ttu-id="7301d-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7301d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7301d-105">&nbsp;&nbsp;[ **\<System. IdentityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="7301d-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="7301d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7301d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="7301d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Tanımlama, ıehandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="7301d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="7301d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Öbek için yığın tanımlama >**</span><span class="sxs-lookup"><span data-stu-id="7301d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7301d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7301d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7301d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7301d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7301d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7301d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7301d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7301d-112">Attributes</span></span>  
  
|<span data-ttu-id="7301d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7301d-113">Attribute</span></span>|<span data-ttu-id="7301d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7301d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7301d-115">Öbek boyutu</span><span class="sxs-lookup"><span data-stu-id="7301d-115">chunkSize</span></span>|<span data-ttu-id="7301d-116">Herhangi bir HTTP tanımlama bilgisinin HTTP tanımlama bilgisi verilerinin karakter cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="7301d-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="7301d-117">Öbek boyutunu ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7301d-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="7301d-118">Web tarayıcıları, her etki alanı için izin verilen tanımlama bilgileri ve sayı boyutları için farklı sınırlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7301d-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="7301d-119">Örneğin, özgün Netscape belirtimi bu sınırları ifade etmek için: 300 tanımlama bilgileri toplamı, tanımlama bilgisi üst bilgisi başına 4096 bayt (meta veriler, yalnızca tanımlama bilgisi değeri değil) ve etki alanı başına 20 tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="7301d-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="7301d-120">Varsayılan değer 2000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7301d-120">The default is 2000.</span></span> <span data-ttu-id="7301d-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7301d-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7301d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7301d-122">Child Elements</span></span>  
 <span data-ttu-id="7301d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="7301d-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7301d-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7301d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7301d-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="7301d-125">Element</span></span>|<span data-ttu-id="7301d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7301d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7301d-127">\<Tanımlama, ıehandler ></span><span class="sxs-lookup"><span data-stu-id="7301d-127">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="7301d-128"><xref:System.IdentityModel.Services.CookieHandler> (Sam)tanımlamabilgileriniokumakveyazmak<xref:System.IdentityModel.Services.SessionAuthenticationModule> için kullandığı öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7301d-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7301d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7301d-129">Remarks</span></span>  
 <span data-ttu-id="7301d-130">Öğesinin özniteliğini "varsayılan" veya "öbekli" olarak <xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` ayarlayarak belirttiğinizde, tanımlama bilgisi işleyicisinin bir `<chunkedCookieHandler>` alt öğe ekleyerek tanımlama bilgilerini okumak ve yazmak için kullandığı öbek boyutunu belirtebilirsiniz. `<cookieHandler>` `chunkSize` özniteliği ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="7301d-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="7301d-131">`<chunkedCookieHandler>` Öğe yoksa, 2000 baytlık varsayılan öbek boyutu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7301d-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="7301d-132">`mode` Öznitelik "Custom" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="7301d-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="7301d-133">`<chunkedCookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7301d-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7301d-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="7301d-134">Example</span></span>  
 <span data-ttu-id="7301d-135">Aşağıdaki örnek, 3000 baytlık öbeklere tanımlama bilgilerini yazan bir öbekli tanımlama bilgisi işleyicisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7301d-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7301d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7301d-136">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
