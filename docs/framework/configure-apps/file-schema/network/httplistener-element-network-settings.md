---
title: "&lt;httpListener&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d880583016e6ccc0ae57fea10c35cb32726c93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lthttplistenergt-element-network-settings"></a><span data-ttu-id="fda8e-102">&lt;httpListener&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="fda8e-102">&lt;httpListener&gt; Element (Network Settings)</span></span>
<span data-ttu-id="fda8e-103">Tarafından kullanılan parametreler özelleştirir <xref:System.Net.HttpListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fda8e-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="fda8e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="fda8e-104">\<configuration></span></span>  
<span data-ttu-id="fda8e-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="fda8e-105">\<system.net></span></span>  
<span data-ttu-id="fda8e-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="fda8e-106">\<settings></span></span>  
<span data-ttu-id="fda8e-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="fda8e-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda8e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fda8e-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="fda8e-109">Tür</span><span class="sxs-lookup"><span data-stu-id="fda8e-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fda8e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fda8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fda8e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fda8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fda8e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fda8e-112">Attributes</span></span>  
  
|<span data-ttu-id="fda8e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fda8e-113">Attribute</span></span>|<span data-ttu-id="fda8e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fda8e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fda8e-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="fda8e-115">unescapeRequestUrl</span></span>|<span data-ttu-id="fda8e-116">Olmadığını gösteren bir Boole değeri bir <xref:System.Net.HttpListener> örneği yerine dönüştürülen URI ham atlanmayan URI kullanır.</span><span class="sxs-lookup"><span data-stu-id="fda8e-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fda8e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fda8e-117">Child Elements</span></span>  
 <span data-ttu-id="fda8e-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="fda8e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fda8e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fda8e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fda8e-120">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="fda8e-120">**Element**</span></span>|<span data-ttu-id="fda8e-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="fda8e-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fda8e-122">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="fda8e-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="fda8e-123">Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fda8e-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fda8e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fda8e-124">Remarks</span></span>  
 <span data-ttu-id="fda8e-125">**UnescapeRequestUrl** öznitelik gösterir <xref:System.Net.HttpListener> ham atlanmayan URI burada tüm yüzde olarak kodlanmış değerler dönüştürülür ve diğer normalleştirme adımları gerçekleştirilecek dönüştürülen URI yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="fda8e-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="fda8e-126">Zaman bir <xref:System.Net.HttpListener> örneği üzerinden bir istek aldığında `http.sys` hizmeti tarafından sağlanan URI dizesinin bir örneğini oluşturur `http.sys`ve olarak ortaya çıkaran <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fda8e-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="fda8e-127">`http.sys` Hizmet sunan iki istek URI dizelerini:</span><span class="sxs-lookup"><span data-stu-id="fda8e-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="fda8e-128">Ham URI</span><span class="sxs-lookup"><span data-stu-id="fda8e-128">Raw URI</span></span>  
  
-   <span data-ttu-id="fda8e-129">Dönüştürülen URI</span><span class="sxs-lookup"><span data-stu-id="fda8e-129">Converted URI</span></span>  
  
 <span data-ttu-id="fda8e-130">Ham URI <xref:System.Uri?displayProperty=nameWithType> bir HTTP isteği isteği satırına:</span><span class="sxs-lookup"><span data-stu-id="fda8e-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="fda8e-131">Tarafından sağlanan ham URI `http.sys` , yukarıda belirtilen istek için "/ yol /".</span><span class="sxs-lookup"><span data-stu-id="fda8e-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="fda8e-132">Bu ağ üzerinden gönderildiği gibi HTTP fiili aşağıdaki dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fda8e-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="fda8e-133">`http.sys` Hizmeti HTTP isteği satırında sağlanan URI kullanılarak isteğinde sağlanan bilgilerden dönüştürülen bir URI oluşturur ve kaynak sunucu isteği belirlemek için ana bilgisayar üstbilgisi iletilmesi gereken.</span><span class="sxs-lookup"><span data-stu-id="fda8e-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="fda8e-134">Bu bilgilerin istek kayıtlı URI ön ek kümesi ile karşılaştırarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fda8e-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="fda8e-135">HTTP sunucusu SDK Belgeleri dönüştürülen bu URI HTTP_COOKED_URL yapısı olarak ifade eder.</span><span class="sxs-lookup"><span data-stu-id="fda8e-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="fda8e-136">Kayıtlı URI önekleri istekle karşılaştırmak oluşturabilmek, istek için bazı normalleştirme yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fda8e-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="fda8e-137">Dönüştürülen URI Yukarıdaki örnek için aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="fda8e-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="fda8e-138">`http.sys` Hizmet birleştirir <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değeri ve dönüştürülen bir URI oluşturmak için istek satırdaki dize.</span><span class="sxs-lookup"><span data-stu-id="fda8e-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="fda8e-139">Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı ayrıca aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="fda8e-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="fda8e-140">Kaydını çıkışları kodlanmış tüm yüzde değerleri.</span><span class="sxs-lookup"><span data-stu-id="fda8e-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="fda8e-141">ASCII olmayan karakterlere UTF-16 karakter gösterimi yüzde olarak kodlanmış dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fda8e-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="fda8e-142">UTF-8 ile ANSI/DBCS karakter (% uXXXX biçimini kullanarak Unicode kodlama) Unicode karakterler yanı sıra desteklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fda8e-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="fda8e-143">Yol sıkıştırma gibi diğer normalleştirme adımları yürütür.</span><span class="sxs-lookup"><span data-stu-id="fda8e-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="fda8e-144">Yüzde olarak kodlanmış değerler için kullanılan kodlamayı hakkında bilgi içermiyor. istek olduğundan, doğru yüzde olarak kodlanmış değerlerin ayrıştırarak kodlama belirlemek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fda8e-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="fda8e-145">Bu nedenle `http.sys` işlemi değiştirmek için iki kayıt defteri anahtarlarını sağlar:</span><span class="sxs-lookup"><span data-stu-id="fda8e-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="fda8e-146">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="fda8e-146">Registry Key</span></span>|<span data-ttu-id="fda8e-147">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="fda8e-147">Default Value</span></span>|<span data-ttu-id="fda8e-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fda8e-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="fda8e-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="fda8e-149">EnableNonUTF8</span></span>|<span data-ttu-id="fda8e-150">1.</span><span class="sxs-lookup"><span data-stu-id="fda8e-150">1</span></span>|<span data-ttu-id="fda8e-151">Sıfır ise, `http.sys` yalnızca UTF-8 olarak kodlanmış URL'leri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="fda8e-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="fda8e-152">Sıfır olursa, `http.sys` de ANSI ile kodlanmış veya DBCS kodlanmış URL'leri istekleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="fda8e-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="fda8e-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="fda8e-153">FavorUTF8</span></span>|<span data-ttu-id="fda8e-154">1.</span><span class="sxs-lookup"><span data-stu-id="fda8e-154">1</span></span>|<span data-ttu-id="fda8e-155">Sıfır olursa, `http.sys` bir URL UTF-8 olarak ilk; bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır kodunu çözmek için her zaman çalışır, Http.sys sonra ANSI veya DBCS olarak çözmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fda8e-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="fda8e-156">Sıfır ise (ve EnableNonUTF8 sıfır olmayan), `http.sys` o varsa ANSI veya DBCS; olarak çözülmesi için deneme başarılı değil, UTF-8 dönüştürme çalışır.</span><span class="sxs-lookup"><span data-stu-id="fda8e-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="fda8e-157">Zaman <xref:System.Net.HttpListener> bir istek alırsa dönüştürülen URI'den kullanan `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fda8e-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="fda8e-158">Karakterleri karakter ve sayıları yanı sıra içinde URI'ler desteklemek için gereksinim yoktur.</span><span class="sxs-lookup"><span data-stu-id="fda8e-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="fda8e-159">Müşteri için müşteri bilgilerini almak için kullanılan aşağıdaki URI örneğidir sayı "1/3812":</span><span class="sxs-lookup"><span data-stu-id="fda8e-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="fda8e-160">Yüzde olarak kodlanmış eğik çizgi (% 2F) URI unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fda8e-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="fda8e-161">Bu durumda veriler ve bir yol ayırıcısı eğik çizgi karakteri temsil ettiği bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fda8e-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="fda8e-162">Dize URI oluşturucusuna geçirerek, aşağıdaki URI olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="fda8e-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="fda8e-163">Yolun kendi kesimler halinde bölme aşağıdaki öğeleri neden olur:</span><span class="sxs-lookup"><span data-stu-id="fda8e-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="fda8e-164">Bu isteği gönderen amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="fda8e-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="fda8e-165">Varsa **unescapeRequestUrl** özniteliği olarak ayarlanmış **false**, sonra ne zaman <xref:System.Net.HttpListener> bir istek alırsa dönüştürülen URI'den yerine ham URI kullanan `http.sys` girişolarak<xref:System.Net.HttpListenerRequest.Url%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fda8e-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="fda8e-166">İçin varsayılan değer **unescapeRequestUrl** özniteliği **doğru**.</span><span class="sxs-lookup"><span data-stu-id="fda8e-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="fda8e-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Özelliği, geçerli değerini almak için kullanılabilir **unescapeRequestUrl** geçerli yapılandırma dosyalarını özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fda8e-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fda8e-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="fda8e-168">Example</span></span>  
 <span data-ttu-id="fda8e-169">Aşağıdaki örnekte nasıl yapılandırılacağını gösterir <xref:System.Net.HttpListener> sınıfı yerine dönüştürülmüş URI'SİNDEN ham URI kullanmak için bir istek aldığında `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fda8e-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="fda8e-170">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="fda8e-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="fda8e-171">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="fda8e-171">Namespace</span></span>|<span data-ttu-id="fda8e-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="fda8e-172">System.Net</span></span>|  
|<span data-ttu-id="fda8e-173">Şema adı</span><span class="sxs-lookup"><span data-stu-id="fda8e-173">Schema Name</span></span>||  
|<span data-ttu-id="fda8e-174">Dosya doğrulama</span><span class="sxs-lookup"><span data-stu-id="fda8e-174">Validation File</span></span>||  
|<span data-ttu-id="fda8e-175">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fda8e-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="fda8e-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fda8e-176">See Also</span></span>  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [<span data-ttu-id="fda8e-177">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fda8e-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
