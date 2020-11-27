---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 2be32591c4844cc6d5d0f02916dd1563bb15dc2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288794"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="d70bd-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d70bd-102">HttpTransportBindingElement</span></span>

<span data-ttu-id="d70bd-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d70bd-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70bd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d70bd-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d70bd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d70bd-105">Methods</span></span>  

 <span data-ttu-id="d70bd-106">HttpTransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d70bd-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d70bd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d70bd-107">Properties</span></span>  

 <span data-ttu-id="d70bd-108">HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d70bd-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="d70bd-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="d70bd-109">AllowCookies</span></span>  

 <span data-ttu-id="d70bd-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d70bd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d70bd-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-112">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d70bd-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="d70bd-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="d70bd-113">AuthenticationScheme</span></span>  

 <span data-ttu-id="d70bd-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d70bd-114">Data type: string</span></span>  
  
 <span data-ttu-id="d70bd-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-116">Bir HTTP dinleyicisi tarafından işlenmekte olan istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="d70bd-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="d70bd-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="d70bd-117">BypassProxyOnLocal</span></span>  

 <span data-ttu-id="d70bd-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d70bd-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d70bd-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-120">Yerel adresler için proxy 'lerin yoksayılıp yoksayılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d70bd-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="d70bd-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d70bd-121">HostNameComparisonMode</span></span>  

 <span data-ttu-id="d70bd-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d70bd-122">Data type: string</span></span>  
  
 <span data-ttu-id="d70bd-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-124">URI üzerinde eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d70bd-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="d70bd-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="d70bd-125">KeepAliveEnabled</span></span>  

 <span data-ttu-id="d70bd-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d70bd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d70bd-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-128">Etkinleştirildiğinde, etkinlik düzeyinden bağımsız olarak HTTP bağlantıları canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="d70bd-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="d70bd-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="d70bd-129">MaxBufferSize</span></span>  

 <span data-ttu-id="d70bd-130">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="d70bd-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="d70bd-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-132">Arabellek havuzunun en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="d70bd-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="d70bd-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="d70bd-133">ProxyAddress</span></span>  

 <span data-ttu-id="d70bd-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d70bd-134">Data type: string</span></span>  
  
 <span data-ttu-id="d70bd-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-136">HTTP istekleri için kullanılacak proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="d70bd-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="d70bd-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="d70bd-137">ProxyAuthenticationScheme</span></span>  

 <span data-ttu-id="d70bd-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d70bd-138">Data type: string</span></span>  
  
 <span data-ttu-id="d70bd-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-140">Bir HTTP proxy tarafından işlenmekte olan istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="d70bd-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="d70bd-141">Bölge</span><span class="sxs-lookup"><span data-stu-id="d70bd-141">Realm</span></span>  

 <span data-ttu-id="d70bd-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d70bd-142">Data type: string</span></span>  
  
 <span data-ttu-id="d70bd-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-144">Kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="d70bd-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="d70bd-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="d70bd-145">TransferMode</span></span>  

 <span data-ttu-id="d70bd-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d70bd-146">Data type: string</span></span>  
  
 <span data-ttu-id="d70bd-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-148">İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d70bd-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="d70bd-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="d70bd-149">UnsafeConnectionNtlmAuthentication</span></span>  

 <span data-ttu-id="d70bd-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d70bd-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="d70bd-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-152">Sunucuda güvenli olmayan bağlantı paylaşımının etkin olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d70bd-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="d70bd-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="d70bd-153">UseDefaultWebProxy</span></span>  

 <span data-ttu-id="d70bd-154">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d70bd-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="d70bd-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d70bd-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d70bd-156">Kullanıcıya özel ayarlar yerine makine genelindeki proxy ayarlarının kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d70bd-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70bd-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d70bd-157">Requirements</span></span>  
  
|<span data-ttu-id="d70bd-158">MOF</span><span class="sxs-lookup"><span data-stu-id="d70bd-158">MOF</span></span>|<span data-ttu-id="d70bd-159">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d70bd-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d70bd-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d70bd-160">Namespace</span></span>|<span data-ttu-id="d70bd-161">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="d70bd-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d70bd-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d70bd-162">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
