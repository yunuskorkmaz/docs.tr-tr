---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 34ad4b8534d082d7f5248d42d70ca5bd0647a5dc
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454323"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="9ed1a-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ed1a-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="9ed1a-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ed1a-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ed1a-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="9ed1a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9ed1a-105">Methods</span></span>  
 <span data-ttu-id="9ed1a-106">HttpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9ed1a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9ed1a-107">Properties</span></span>  
 <span data-ttu-id="9ed1a-108">HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9ed1a-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="9ed1a-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="9ed1a-109">AllowCookies</span></span>  
 <span data-ttu-id="9ed1a-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9ed1a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="9ed1a-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-112">İstemci tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="9ed1a-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="9ed1a-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="9ed1a-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-114">Data type: string</span></span>  
  
 <span data-ttu-id="9ed1a-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-116">HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="9ed1a-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="9ed1a-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="9ed1a-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9ed1a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="9ed1a-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-120">Yerel adresler için proxy yoksayılıp sayılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="9ed1a-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="9ed1a-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="9ed1a-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-122">Data type: string</span></span>  
  
 <span data-ttu-id="9ed1a-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-124">Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="9ed1a-125">keepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="9ed1a-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="9ed1a-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9ed1a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="9ed1a-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-128">Etkinleştirildiğinde, HTTP bağlantıları canlı etkinlik düzeyinden bağımsız olarak tutulur.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="9ed1a-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-129">MaxBufferSize</span></span>  
 <span data-ttu-id="9ed1a-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9ed1a-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="9ed1a-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-132">Arabellek havuzu maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="9ed1a-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="9ed1a-133">ProxyAddress</span></span>  
 <span data-ttu-id="9ed1a-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-134">Data type: string</span></span>  
  
 <span data-ttu-id="9ed1a-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-136">HTTP istekleri için kullanılacak proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="9ed1a-137">proxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="9ed1a-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="9ed1a-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-138">Data type: string</span></span>  
  
 <span data-ttu-id="9ed1a-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-140">HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="9ed1a-141">Bölge</span><span class="sxs-lookup"><span data-stu-id="9ed1a-141">Realm</span></span>  
 <span data-ttu-id="9ed1a-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-142">Data type: string</span></span>  
  
 <span data-ttu-id="9ed1a-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-144">Kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="9ed1a-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="9ed1a-145">TransferMode</span></span>  
 <span data-ttu-id="9ed1a-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9ed1a-146">Data type: string</span></span>  
  
 <span data-ttu-id="9ed1a-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-148">İletileri ara belleğe veya akışa veya bir istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="9ed1a-149">unsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="9ed1a-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="9ed1a-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9ed1a-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="9ed1a-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-152">Güvensiz bağlantı paylaşımının sunucu üzerinde etkin olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="9ed1a-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="9ed1a-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="9ed1a-154">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9ed1a-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="9ed1a-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9ed1a-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ed1a-156">Makine genelindeki proxy ayarlarının kullanıcıya özel ayarlar yerine kullanılır olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed1a-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ed1a-157">Requirements</span></span>  
  
|<span data-ttu-id="9ed1a-158">MOF</span><span class="sxs-lookup"><span data-stu-id="9ed1a-158">MOF</span></span>|<span data-ttu-id="9ed1a-159">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9ed1a-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9ed1a-160">Namespace</span></span>|<span data-ttu-id="9ed1a-161">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9ed1a-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ed1a-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed1a-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
