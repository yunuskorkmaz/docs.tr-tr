---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 1975fd2e04a5c9cdb68bc838802abafbd781b7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487026"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="dbe7d-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dbe7d-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="dbe7d-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dbe7d-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbe7d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="dbe7d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dbe7d-105">Methods</span></span>  
 <span data-ttu-id="dbe7d-106">HttpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dbe7d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="dbe7d-107">Properties</span></span>  
 <span data-ttu-id="dbe7d-108">HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dbe7d-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="dbe7d-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="dbe7d-109">AllowCookies</span></span>  
 <span data-ttu-id="dbe7d-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="dbe7d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="dbe7d-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-112">İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="dbe7d-113">authenticationScheme</span><span class="sxs-lookup"><span data-stu-id="dbe7d-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="dbe7d-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-114">Data type: string</span></span>  
  
 <span data-ttu-id="dbe7d-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-116">Bir HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="dbe7d-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="dbe7d-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="dbe7d-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="dbe7d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="dbe7d-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-120">Yerel adresler için proxy yoksayılır olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="dbe7d-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="dbe7d-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="dbe7d-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-122">Data type: string</span></span>  
  
 <span data-ttu-id="dbe7d-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-124">Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="dbe7d-125">keepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="dbe7d-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="dbe7d-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="dbe7d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="dbe7d-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-128">Etkinleştirildiğinde, HTTP bağlantılarını etkinlik düzeyi bağımsız olarak Canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="dbe7d-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-129">MaxBufferSize</span></span>  
 <span data-ttu-id="dbe7d-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="dbe7d-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="dbe7d-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-132">Arabellek havuzu en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="dbe7d-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="dbe7d-133">ProxyAddress</span></span>  
 <span data-ttu-id="dbe7d-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-134">Data type: string</span></span>  
  
 <span data-ttu-id="dbe7d-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-136">HTTP istekleri için kullanılacak proxy adresi içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="dbe7d-137">proxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="dbe7d-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="dbe7d-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-138">Data type: string</span></span>  
  
 <span data-ttu-id="dbe7d-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-140">Bir HTTP proxy'si tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="dbe7d-141">Bölge</span><span class="sxs-lookup"><span data-stu-id="dbe7d-141">Realm</span></span>  
 <span data-ttu-id="dbe7d-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-142">Data type: string</span></span>  
  
 <span data-ttu-id="dbe7d-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-144">Kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="dbe7d-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="dbe7d-145">TransferMode</span></span>  
 <span data-ttu-id="dbe7d-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="dbe7d-146">Data type: string</span></span>  
  
 <span data-ttu-id="dbe7d-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-148">İletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="dbe7d-149">unsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="dbe7d-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="dbe7d-150">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="dbe7d-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="dbe7d-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-152">Güvenli bağlantı paylaşımı sunucu üzerinde etkin olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="dbe7d-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="dbe7d-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="dbe7d-154">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="dbe7d-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="dbe7d-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="dbe7d-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dbe7d-156">Makine genelinde proxy ayarlarını yerine kullanıcıya özgü ayarları kullanılıp kullanılmayacağını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe7d-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbe7d-157">Requirements</span></span>  
  
|<span data-ttu-id="dbe7d-158">MOF</span><span class="sxs-lookup"><span data-stu-id="dbe7d-158">MOF</span></span>|<span data-ttu-id="dbe7d-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dbe7d-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="dbe7d-160">Namespace</span></span>|<span data-ttu-id="dbe7d-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dbe7d-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbe7d-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe7d-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
