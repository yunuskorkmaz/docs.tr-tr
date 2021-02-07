---
description: 'Daha fazla bilgi edinin: HttpTransportBindingElement'
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 6c516dd7124d52828145787d55421d12031c2d36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757377"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="c8c09-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c8c09-103">HttpTransportBindingElement</span></span>

<span data-ttu-id="c8c09-104">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c8c09-104">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c09-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8c09-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="c8c09-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c8c09-106">Methods</span></span>  

 <span data-ttu-id="c8c09-107">HttpTransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="c8c09-107">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c8c09-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c8c09-108">Properties</span></span>  

 <span data-ttu-id="c8c09-109">HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c8c09-109">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="c8c09-110">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="c8c09-110">AllowCookies</span></span>  

 <span data-ttu-id="c8c09-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="c8c09-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="c8c09-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-113">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c8c09-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="c8c09-114">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="c8c09-114">AuthenticationScheme</span></span>  

 <span data-ttu-id="c8c09-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="c8c09-115">Data type: string</span></span>  
  
 <span data-ttu-id="c8c09-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-117">Bir HTTP dinleyicisi tarafından işlenmekte olan istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="c8c09-117">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="c8c09-118">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c8c09-118">BypassProxyOnLocal</span></span>  

 <span data-ttu-id="c8c09-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="c8c09-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="c8c09-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-121">Yerel adresler için proxy 'lerin yoksayılıp yoksayılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c8c09-121">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="c8c09-122">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c8c09-122">HostNameComparisonMode</span></span>  

 <span data-ttu-id="c8c09-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="c8c09-123">Data type: string</span></span>  
  
 <span data-ttu-id="c8c09-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-125">URI üzerinde eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c8c09-125">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="c8c09-126">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="c8c09-126">KeepAliveEnabled</span></span>  

 <span data-ttu-id="c8c09-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="c8c09-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="c8c09-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-129">Etkinleştirildiğinde, etkinlik düzeyinden bağımsız olarak HTTP bağlantıları canlı tutulur.</span><span class="sxs-lookup"><span data-stu-id="c8c09-129">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="c8c09-130">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c8c09-130">MaxBufferSize</span></span>  

 <span data-ttu-id="c8c09-131">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="c8c09-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="c8c09-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-133">Arabellek havuzunun en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="c8c09-133">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="c8c09-134">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="c8c09-134">ProxyAddress</span></span>  

 <span data-ttu-id="c8c09-135">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="c8c09-135">Data type: string</span></span>  
  
 <span data-ttu-id="c8c09-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-137">HTTP istekleri için kullanılacak proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="c8c09-137">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="c8c09-138">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="c8c09-138">ProxyAuthenticationScheme</span></span>  

 <span data-ttu-id="c8c09-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="c8c09-139">Data type: string</span></span>  
  
 <span data-ttu-id="c8c09-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-141">Bir HTTP proxy tarafından işlenmekte olan istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="c8c09-141">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="c8c09-142">Bölge</span><span class="sxs-lookup"><span data-stu-id="c8c09-142">Realm</span></span>  

 <span data-ttu-id="c8c09-143">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="c8c09-143">Data type: string</span></span>  
  
 <span data-ttu-id="c8c09-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-145">Kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="c8c09-145">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="c8c09-146">TransferMode</span><span class="sxs-lookup"><span data-stu-id="c8c09-146">TransferMode</span></span>  

 <span data-ttu-id="c8c09-147">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="c8c09-147">Data type: string</span></span>  
  
 <span data-ttu-id="c8c09-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-149">İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c8c09-149">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="c8c09-150">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="c8c09-150">UnsafeConnectionNtlmAuthentication</span></span>  

 <span data-ttu-id="c8c09-151">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="c8c09-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="c8c09-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-153">Sunucuda güvenli olmayan bağlantı paylaşımının etkin olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c8c09-153">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="c8c09-154">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c8c09-154">UseDefaultWebProxy</span></span>  

 <span data-ttu-id="c8c09-155">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="c8c09-155">Data type: boolean</span></span>  
  
 <span data-ttu-id="c8c09-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c8c09-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8c09-157">Kullanıcıya özel ayarlar yerine makine genelindeki proxy ayarlarının kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c8c09-157">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8c09-158">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8c09-158">Requirements</span></span>  
  
|<span data-ttu-id="c8c09-159">MOF</span><span class="sxs-lookup"><span data-stu-id="c8c09-159">MOF</span></span>|<span data-ttu-id="c8c09-160">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c8c09-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c8c09-161">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="c8c09-161">Namespace</span></span>|<span data-ttu-id="c8c09-162">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="c8c09-162">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8c09-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8c09-163">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
