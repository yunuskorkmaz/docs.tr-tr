---
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: b3a6d527bc1bf8210bb85424fa218fda495a2a2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099751"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="2c0f7-102">\<httpListener > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="2c0f7-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="2c0f7-103">Tarafından kullanılan parametreler özelleştirir <xref:System.Net.HttpListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="2c0f7-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="2c0f7-104">\<configuration></span></span>  
<span data-ttu-id="2c0f7-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2c0f7-105">\<system.net></span></span>  
<span data-ttu-id="2c0f7-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="2c0f7-106">\<settings></span></span>  
<span data-ttu-id="2c0f7-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="2c0f7-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0f7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c0f7-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="2c0f7-109">Tür</span><span class="sxs-lookup"><span data-stu-id="2c0f7-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c0f7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c0f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c0f7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c0f7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c0f7-112">Attributes</span></span>  
  
|<span data-ttu-id="2c0f7-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c0f7-113">Attribute</span></span>|<span data-ttu-id="2c0f7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c0f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c0f7-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="2c0f7-115">unescapeRequestUrl</span></span>|<span data-ttu-id="2c0f7-116">Olmadığını gösteren bir Boole değeri bir <xref:System.Net.HttpListener> örneği yerine dönüştürülmüş URI ham atlanmayan URI kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c0f7-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c0f7-117">Child Elements</span></span>  
 <span data-ttu-id="2c0f7-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c0f7-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c0f7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2c0f7-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2c0f7-120">**Element**</span></span>|<span data-ttu-id="2c0f7-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2c0f7-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2c0f7-122">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="2c0f7-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="2c0f7-123">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c0f7-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c0f7-124">Remarks</span></span>  
 <span data-ttu-id="2c0f7-125">**UnescapeRequestUrl** özniteliği gösterir <xref:System.Net.HttpListener> ham atlanmayan URI burada herhangi bir yüzde olarak kodlanmış değerler dönüştürülür ve diğer normalleştirme adımları alınır dönüştürülmüş URI yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="2c0f7-126">Olduğunda bir <xref:System.Net.HttpListener> örneği bir talep aldığında `http.sys` hizmeti tarafından sağlanan URI dizesinin bir örneğini oluşturur `http.sys`ve olarak kullanıma sunduğu <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="2c0f7-127">`http.sys` Hizmetini iki istek URI dizelerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="2c0f7-128">Ham URI'si</span><span class="sxs-lookup"><span data-stu-id="2c0f7-128">Raw URI</span></span>  
  
-   <span data-ttu-id="2c0f7-129">Dönüştürülen URI'si</span><span class="sxs-lookup"><span data-stu-id="2c0f7-129">Converted URI</span></span>  
  
 <span data-ttu-id="2c0f7-130">Ham URI <xref:System.Uri?displayProperty=nameWithType> bir HTTP isteğinin istek satırında sağlanan:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="2c0f7-131">Tarafından sağlanan ham URI `http.sys` , yukarıda belirtilen istek için "/ path /".</span><span class="sxs-lookup"><span data-stu-id="2c0f7-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="2c0f7-132">Bu, HTTP fiili olarak ağ üzerinden gönderilen aşağıdaki dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="2c0f7-133">`http.sys` Hizmeti HTTP isteği satırında sağlanan URI kullanılarak istekte sağlanan bilgileri dönüştürülen bir URI oluşturur ve kaynak sunucu isteği belirlemek için ana bilgisayar üstbilgisi iletilmesi.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="2c0f7-134">Bu bilgilerin istek kayıtlı URI ön ek kümesi ile karşılaştırarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="2c0f7-135">HTTP sunucusu SDK Belgeleri HTTP_COOKED_URL yapısı olarak dönüştürülen bu URI'ye ifade eder.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="2c0f7-136">Kayıtlı URI ön ekine sahip istek karşılaştırma mümkün olması için bazı normalleştirme isteğine yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="2c0f7-137">Dönüştürülen URI Yukarıdaki örnek şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="2c0f7-138">`http.sys` Hizmet birleştirir <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değeri ve dönüştürülen bir URI oluşturmak için istek satırı dizesini.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="2c0f7-139">Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı aynı zamanda şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="2c0f7-140">Geri Al çıkışları kodlanmış tüm yüzde değerleri.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="2c0f7-141">Yüzde olarak kodlanmış dönüştüren ASCII olmayan karakterler bir UTF-16 karakter temsili.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="2c0f7-142">UTF-8 ve ANSI/DBCS karakterlerin yanı sıra Unicode karakter (Unicode kodlama % uXXXX biçimini kullanarak) desteklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="2c0f7-143">Yol sıkıştırma gibi diğer normalleştirme adımları yürütür.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="2c0f7-144">İstek değerlerini yüzde olarak kodlanmış kullanılan kodlama hakkında bilgi içermiyor olduğundan, doğru yüzde olarak kodlanmış değerler ayrıştırarak kodlama belirlemek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="2c0f7-145">Bu nedenle `http.sys` iki kayıt defteri anahtarlarını değiştirme işlemi sağlar:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="2c0f7-146">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="2c0f7-146">Registry Key</span></span>|<span data-ttu-id="2c0f7-147">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="2c0f7-147">Default Value</span></span>|<span data-ttu-id="2c0f7-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c0f7-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="2c0f7-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="2c0f7-149">EnableNonUTF8</span></span>|<span data-ttu-id="2c0f7-150">1.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-150">1</span></span>|<span data-ttu-id="2c0f7-151">Sıfır ise `http.sys` yalnızca UTF-8 olarak kodlanmış URL'ler kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="2c0f7-152">Sıfır olmayan, `http.sys` isteklerinde ANSI kodlu veya DBCS kodlu URL'leri de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="2c0f7-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="2c0f7-153">FavorUTF8</span></span>|<span data-ttu-id="2c0f7-154">1.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-154">1</span></span>|<span data-ttu-id="2c0f7-155">Sıfır olmayan, `http.sys` bir URL UTF-8 ilk; bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır olmayan kod çözme için her zaman çalışır, Http.sys sonra ANSI veya DBCS olarak çözmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="2c0f7-156">Sıfır ise (ve EnableNonUTF8 sıfır olmayan), `http.sys` durumunda ANSI veya DBCS; olarak çözülmesi için deneme başarılı değil, UTF-8 dönüştürme çalışır.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="2c0f7-157">Zaman <xref:System.Net.HttpListener> bir istek alırsa dönüştürülmüş URI'SİNDEN kullanan `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="2c0f7-158">Karakterler ve numaralar yanı sıra karakterleri Urılar içinde desteklemek için bir gereksinim yoktur.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="2c0f7-159">Müşteri için müşteri bilgilerini almak için kullanılan aşağıdaki URI örneğidir "1/3812" sayı:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="2c0f7-160">Yüzde olarak kodlanmış eğik çizgi (% 2F) uri'sindeki unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="2c0f7-161">Bu durumda veri ve yol sınırlayıcısını eğik çizgi karakteri temsil ettiği bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="2c0f7-162">Dize URI oluşturucusuna geçirerek, aşağıdaki URI olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="2c0f7-163">Yol segmentlerini bölme, aşağıdaki öğeleri neden olur:</span><span class="sxs-lookup"><span data-stu-id="2c0f7-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="2c0f7-164">Bu isteği gönderen amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="2c0f7-165">Varsa **unescapeRequestUrl** özniteliği **false**, sonra ne zaman <xref:System.Net.HttpListener> bir istek alırsa yerine dönüştürülmüş URI'SİNDEN ham URI kullanan `http.sys` girişolarak<xref:System.Net.HttpListenerRequest.Url%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="2c0f7-166">İçin varsayılan değer **unescapeRequestUrl** özniteliği **true**.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="2c0f7-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Özelliği, geçerli değerini almak için kullanılabilir **unescapeRequestUrl** ilgili yapılandırma dosyaları özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c0f7-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c0f7-168">Example</span></span>  
 <span data-ttu-id="2c0f7-169">Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.Net.HttpListener> sınıfı yerine dönüştürülmüş URI'SİNDEN ham URI kullanmak için bir istek aldığında `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="2c0f7-170">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="2c0f7-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="2c0f7-171">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2c0f7-171">Namespace</span></span>|<span data-ttu-id="2c0f7-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="2c0f7-172">System.Net</span></span>|  
|<span data-ttu-id="2c0f7-173">Şema adı</span><span class="sxs-lookup"><span data-stu-id="2c0f7-173">Schema Name</span></span>||  
|<span data-ttu-id="2c0f7-174">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="2c0f7-174">Validation File</span></span>||  
|<span data-ttu-id="2c0f7-175">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="2c0f7-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c0f7-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="2c0f7-177">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2c0f7-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
