---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: a321c10e04eca2c1a5204929966a1725e918cbdf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158532"
---
# \<chunkedCookieHandler>

<span data-ttu-id="95093-101">Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="95093-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="95093-102">Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="95093-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="95093-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="95093-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95093-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95093-104">Attributes and Elements</span></span>  

 <span data-ttu-id="95093-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95093-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95093-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95093-106">Attributes</span></span>  
  
|<span data-ttu-id="95093-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="95093-107">Attribute</span></span>|<span data-ttu-id="95093-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95093-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95093-109">Öbek boyutu</span><span class="sxs-lookup"><span data-stu-id="95093-109">chunkSize</span></span>|<span data-ttu-id="95093-110">Herhangi bir HTTP tanımlama bilgisinin HTTP tanımlama bilgisi verilerinin karakter cinsinden en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="95093-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="95093-111">Öbek boyutunu ayarlarken dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95093-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="95093-112">Web tarayıcıları, her etki alanı için izin verilen tanımlama bilgileri ve sayı boyutları için farklı sınırlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95093-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="95093-113">Örneğin, özgün Netscape belirtimi bu limitleri sınırlar: 300 tanımlama bilgileri toplamı, tanımlama bilgisi üstbilgisi başına 4096 bayt (meta veriler dahil, yalnızca tanımlama bilgisi değerini değil) ve etki alanı başına 20 tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="95093-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="95093-114">Varsayılan değer 2000’dir.</span><span class="sxs-lookup"><span data-stu-id="95093-114">The default is 2000.</span></span> <span data-ttu-id="95093-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="95093-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95093-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95093-116">Child Elements</span></span>  

 <span data-ttu-id="95093-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="95093-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95093-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95093-118">Parent Elements</span></span>  
  
|<span data-ttu-id="95093-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="95093-119">Element</span></span>|<span data-ttu-id="95093-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95093-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="95093-121"><xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) tanımlama bilgilerini okumak ve yazmak için kullandığı öğesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="95093-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95093-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95093-122">Remarks</span></span>  

 <span data-ttu-id="95093-123"><xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` `<cookieHandler>` Öğesinin özniteliğini "varsayılan" veya "öbekli" olarak ayarlayarak belirttiğinizde, tanımlama bilgisi işleyicisinin bir `<chunkedCookieHandler>` alt öğe ekleyerek ve özniteliğini ayarlayarak tanımlama bilgilerini okumak ve yazmak için kullandığı öbek boyutunu belirtebilirsiniz `chunkSize` .</span><span class="sxs-lookup"><span data-stu-id="95093-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="95093-124">`<chunkedCookieHandler>`Öğe yoksa, 2000 baytlık varsayılan öbek boyutu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95093-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="95093-125">`mode`Öznitelik "Custom" olarak ayarlandığında bu öğe belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="95093-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="95093-126">`<chunkedCookieHandler>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> .</span><span class="sxs-lookup"><span data-stu-id="95093-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95093-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="95093-127">Example</span></span>  

 <span data-ttu-id="95093-128">Aşağıdaki örnek, 3000 baytlık öbeklere tanımlama bilgilerini yazan bir öbekli tanımlama bilgisi işleyicisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="95093-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95093-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95093-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
