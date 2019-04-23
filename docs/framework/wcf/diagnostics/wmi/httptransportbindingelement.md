---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 5e23342d57621554aaec67c5c568bb75202a9454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977047"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="71ed9-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="71ed9-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="71ed9-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="71ed9-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ed9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71ed9-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="71ed9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71ed9-105">Methods</span></span>  
 <span data-ttu-id="71ed9-106">HttpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="71ed9-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="71ed9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="71ed9-107">Properties</span></span>  
 <span data-ttu-id="71ed9-108">HttpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="71ed9-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="71ed9-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="71ed9-109">AllowCookies</span></span>  
 <span data-ttu-id="71ed9-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="71ed9-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="71ed9-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-112">İstemci tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="71ed9-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="71ed9-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="71ed9-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="71ed9-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71ed9-114">Data type: string</span></span>  
  
 <span data-ttu-id="71ed9-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-116">HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="71ed9-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="71ed9-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="71ed9-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="71ed9-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="71ed9-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="71ed9-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-120">Yerel adresler için proxy yoksayılıp sayılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="71ed9-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="71ed9-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="71ed9-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="71ed9-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71ed9-122">Data type: string</span></span>  
  
 <span data-ttu-id="71ed9-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-124">Ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="71ed9-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="71ed9-125">keepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="71ed9-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="71ed9-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="71ed9-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="71ed9-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-128">Etkinleştirildiğinde, HTTP bağlantıları canlı etkinlik düzeyinden bağımsız olarak tutulur.</span><span class="sxs-lookup"><span data-stu-id="71ed9-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="71ed9-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="71ed9-129">MaxBufferSize</span></span>  
 <span data-ttu-id="71ed9-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="71ed9-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="71ed9-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-132">Arabellek havuzu maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="71ed9-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="71ed9-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="71ed9-133">ProxyAddress</span></span>  
 <span data-ttu-id="71ed9-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71ed9-134">Data type: string</span></span>  
  
 <span data-ttu-id="71ed9-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-136">HTTP istekleri için kullanılacak proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="71ed9-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="71ed9-137">proxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="71ed9-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="71ed9-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71ed9-138">Data type: string</span></span>  
  
 <span data-ttu-id="71ed9-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-140">HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="71ed9-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="71ed9-141">Bölge</span><span class="sxs-lookup"><span data-stu-id="71ed9-141">Realm</span></span>  
 <span data-ttu-id="71ed9-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71ed9-142">Data type: string</span></span>  
  
 <span data-ttu-id="71ed9-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-144">Kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="71ed9-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="71ed9-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="71ed9-145">TransferMode</span></span>  
 <span data-ttu-id="71ed9-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="71ed9-146">Data type: string</span></span>  
  
 <span data-ttu-id="71ed9-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-148">İletileri ara belleğe veya akışa veya bir istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="71ed9-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="71ed9-149">unsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="71ed9-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="71ed9-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="71ed9-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="71ed9-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-152">Güvensiz bağlantı paylaşımının sunucu üzerinde etkin olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="71ed9-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="71ed9-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="71ed9-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="71ed9-154">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="71ed9-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="71ed9-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="71ed9-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="71ed9-156">Makine genelindeki proxy ayarlarının kullanıcıya özel ayarlar yerine kullanılır olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="71ed9-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71ed9-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71ed9-157">Requirements</span></span>  
  
|<span data-ttu-id="71ed9-158">MOF</span><span class="sxs-lookup"><span data-stu-id="71ed9-158">MOF</span></span>|<span data-ttu-id="71ed9-159">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="71ed9-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="71ed9-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="71ed9-160">Namespace</span></span>|<span data-ttu-id="71ed9-161">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="71ed9-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71ed9-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71ed9-162">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
