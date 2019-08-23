---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b3b4cf0d7c2748079af7a94534622b1dbadd3ab5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941887"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="c2adf-101">\<Öbek için yığın tanımlama ></span><span class="sxs-lookup"><span data-stu-id="c2adf-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="c2adf-102">Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="c2adf-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="c2adf-103">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c2adf-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="c2adf-104">\<System. IdentityModel. Services ></span><span class="sxs-lookup"><span data-stu-id="c2adf-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="c2adf-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c2adf-105">\<federationConfiguration></span></span>  
<span data-ttu-id="c2adf-106">\<Tanımlama, ıehandler ></span><span class="sxs-lookup"><span data-stu-id="c2adf-106">\<cookieHandler></span></span>  
<span data-ttu-id="c2adf-107">\<Öbek için yığın tanımlama ></span><span class="sxs-lookup"><span data-stu-id="c2adf-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2adf-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2adf-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2adf-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2adf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c2adf-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2adf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2adf-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2adf-111">Attributes</span></span>  
  
|<span data-ttu-id="c2adf-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c2adf-112">Attribute</span></span>|<span data-ttu-id="c2adf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2adf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2adf-114">Öbek boyutu</span><span class="sxs-lookup"><span data-stu-id="c2adf-114">chunkSize</span></span>|<span data-ttu-id="c2adf-115">Herhangi bir HTTP tanımlama bilgisinin HTTP tanımlama bilgisi verilerinin karakter cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="c2adf-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="c2adf-116">Öbek boyutunu ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2adf-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="c2adf-117">Web tarayıcıları, her etki alanı için izin verilen tanımlama bilgileri ve sayı boyutları için farklı sınırlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c2adf-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="c2adf-118">Örneğin, özgün Netscape belirtimi bu sınırları ifade etmek için: 300 tanımlama bilgileri toplamı, tanımlama bilgisi üst bilgisi başına 4096 bayt (meta veriler, yalnızca tanımlama bilgisi değeri değil) ve etki alanı başına 20 tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="c2adf-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="c2adf-119">Varsayılan değer 2000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c2adf-119">The default is 2000.</span></span> <span data-ttu-id="c2adf-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2adf-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2adf-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2adf-121">Child Elements</span></span>  
 <span data-ttu-id="c2adf-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="c2adf-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2adf-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2adf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c2adf-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c2adf-124">Element</span></span>|<span data-ttu-id="c2adf-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2adf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2adf-126">\<Tanımlama, ıehandler ></span><span class="sxs-lookup"><span data-stu-id="c2adf-126">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="c2adf-127"><xref:System.IdentityModel.Services.CookieHandler> (Sam)tanımlamabilgileriniokumakveyazmak<xref:System.IdentityModel.Services.SessionAuthenticationModule> için kullandığı öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c2adf-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2adf-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2adf-128">Remarks</span></span>  
 <span data-ttu-id="c2adf-129">Öğesinin özniteliğini "varsayılan" veya "öbekli" olarak <xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` ayarlayarak belirttiğinizde, tanımlama bilgisi işleyicisinin bir `<chunkedCookieHandler>` alt öğe ekleyerek tanımlama bilgilerini okumak ve yazmak için kullandığı öbek boyutunu belirtebilirsiniz. `<cookieHandler>` `chunkSize` özniteliği ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="c2adf-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="c2adf-130">`<chunkedCookieHandler>` Öğe yoksa, 2000 baytlık varsayılan öbek boyutu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2adf-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="c2adf-131">`mode` Öznitelik "Custom" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="c2adf-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="c2adf-132">`<chunkedCookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c2adf-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2adf-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2adf-133">Example</span></span>  
 <span data-ttu-id="c2adf-134">Aşağıdaki örnek, 3000 baytlık öbeklere tanımlama bilgilerini yazan bir öbekli tanımlama bilgisi işleyicisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c2adf-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2adf-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2adf-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
