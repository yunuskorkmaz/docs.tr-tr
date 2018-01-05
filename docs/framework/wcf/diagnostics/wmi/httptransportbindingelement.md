---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6370284dbd9c680b29f315c791ea76356e7b36f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="cff5b-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="cff5b-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="cff5b-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="cff5b-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cff5b-104">Syntax</span></span>  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cff5b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cff5b-105">Methods</span></span>  
 <span data-ttu-id="cff5b-106">HttpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cff5b-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cff5b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cff5b-107">Properties</span></span>  
 <span data-ttu-id="cff5b-108">HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cff5b-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="cff5b-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="cff5b-109">AllowCookies</span></span>  
 <span data-ttu-id="cff5b-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cff5b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="cff5b-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-112">İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cff5b-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="cff5b-113">authenticationScheme</span><span class="sxs-lookup"><span data-stu-id="cff5b-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="cff5b-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cff5b-114">Data type: string</span></span>  
  
 <span data-ttu-id="cff5b-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-116">Bir HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="cff5b-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="cff5b-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="cff5b-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="cff5b-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cff5b-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cff5b-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-120">Yerel adresler için proxy yoksayılır olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cff5b-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="cff5b-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="cff5b-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="cff5b-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cff5b-122">Data type: string</span></span>  
  
 <span data-ttu-id="cff5b-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-124">Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="cff5b-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="cff5b-125">keepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="cff5b-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="cff5b-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cff5b-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="cff5b-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-128">Etkinleştirildiğinde, HTTP bağlantılarını etkinlik düzeyi bağımsız olarak Canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="cff5b-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="cff5b-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="cff5b-129">MaxBufferSize</span></span>  
 <span data-ttu-id="cff5b-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cff5b-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="cff5b-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-132">Arabellek havuzu en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="cff5b-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="cff5b-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="cff5b-133">ProxyAddress</span></span>  
 <span data-ttu-id="cff5b-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cff5b-134">Data type: string</span></span>  
  
 <span data-ttu-id="cff5b-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-136">HTTP istekleri için kullanılacak proxy adresi içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="cff5b-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="cff5b-137">proxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="cff5b-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="cff5b-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cff5b-138">Data type: string</span></span>  
  
 <span data-ttu-id="cff5b-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-140">Bir HTTP proxy'si tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="cff5b-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="cff5b-141">Bölge</span><span class="sxs-lookup"><span data-stu-id="cff5b-141">Realm</span></span>  
 <span data-ttu-id="cff5b-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cff5b-142">Data type: string</span></span>  
  
 <span data-ttu-id="cff5b-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-144">Kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="cff5b-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="cff5b-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="cff5b-145">TransferMode</span></span>  
 <span data-ttu-id="cff5b-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cff5b-146">Data type: string</span></span>  
  
 <span data-ttu-id="cff5b-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-148">İletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="cff5b-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="cff5b-149">unsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="cff5b-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="cff5b-150">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cff5b-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="cff5b-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-152">Güvenli bağlantı paylaşımı sunucu üzerinde etkin olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cff5b-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="cff5b-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="cff5b-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="cff5b-154">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cff5b-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="cff5b-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cff5b-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cff5b-156">Makine genelinde proxy ayarlarını yerine kullanıcıya özgü ayarları kullanılıp kullanılmayacağını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="cff5b-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff5b-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cff5b-157">Requirements</span></span>  
  
|<span data-ttu-id="cff5b-158">MOF</span><span class="sxs-lookup"><span data-stu-id="cff5b-158">MOF</span></span>|<span data-ttu-id="cff5b-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cff5b-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cff5b-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cff5b-160">Namespace</span></span>|<span data-ttu-id="cff5b-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cff5b-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cff5b-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cff5b-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
