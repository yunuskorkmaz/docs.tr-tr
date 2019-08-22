---
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: cb24dc7296e2f2f6ea292566330d3d6ae4f25f85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664133"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="dbe20-102">\<httpListener > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="dbe20-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="dbe20-103"><xref:System.Net.HttpListener> Sınıf tarafından kullanılan parametreleri özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="dbe20-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="dbe20-104">\<configuration></span></span>  
<span data-ttu-id="dbe20-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="dbe20-105">\<system.net></span></span>  
<span data-ttu-id="dbe20-106">\<Ayarlar ></span><span class="sxs-lookup"><span data-stu-id="dbe20-106">\<settings></span></span>  
<span data-ttu-id="dbe20-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="dbe20-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe20-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbe20-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="dbe20-109">Tür</span><span class="sxs-lookup"><span data-stu-id="dbe20-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbe20-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbe20-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dbe20-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbe20-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbe20-112">Attributes</span></span>  
  
|<span data-ttu-id="dbe20-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbe20-113">Attribute</span></span>|<span data-ttu-id="dbe20-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbe20-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbe20-115">unescapeRequestUrl 'Si</span><span class="sxs-lookup"><span data-stu-id="dbe20-115">unescapeRequestUrl</span></span>|<span data-ttu-id="dbe20-116">Bir <xref:System.Net.HttpListener> Örneğin, dönüştürülmüş URI yerine ham unatsız URI kullanıp kullanmadığını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="dbe20-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbe20-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbe20-117">Child Elements</span></span>  
 <span data-ttu-id="dbe20-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbe20-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbe20-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbe20-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dbe20-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="dbe20-120">**Element**</span></span>|<span data-ttu-id="dbe20-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="dbe20-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dbe20-122">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="dbe20-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="dbe20-123"><xref:System.Net> Ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe20-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbe20-124">Remarks</span></span>  
 <span data-ttu-id="dbe20-125">**UnescapeRequestUrl** özniteliği, yüzde kodlamalı <xref:System.Net.HttpListener> değerlerin dönüştürüldüğü ve diğer normalleştirme adımlarının alındığı dönüştürülmüş URI yerine, ham kaçışsız URI kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="dbe20-126">Bir <xref:System.Net.HttpListener> örnek `http.sys` hizmet aracılığıyla bir istek aldığında, tarafından `http.sys`sağlanmış URI dizesinin bir örneğini oluşturur ve <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="dbe20-127">`http.sys` Hizmet iki istek URI dizesini kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="dbe20-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="dbe20-128">Ham URI</span><span class="sxs-lookup"><span data-stu-id="dbe20-128">Raw URI</span></span>  
  
- <span data-ttu-id="dbe20-129">Dönüştürülmüş URI</span><span class="sxs-lookup"><span data-stu-id="dbe20-129">Converted URI</span></span>  
  
 <span data-ttu-id="dbe20-130">Ham URI <xref:System.Uri?displayProperty=nameWithType> , http isteğinin istek satırında verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dbe20-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="dbe20-131">Yukarıda belirtilen istek için tarafından `http.sys` belirtilen ham URI, "/path/" dir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="dbe20-132">Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dbe20-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="dbe20-133">`http.sys` Hizmet, isteğin iletilmesi gereken kaynak sunucuyu belirleyebilmek için http istek satırında ve ana bilgisayar üstbilgisinde belirtilen URI 'yi kullanarak istekte belirtilen bilgilerden dönüştürülmüş bir URI oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbe20-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="dbe20-134">Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="dbe20-135">HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.</span><span class="sxs-lookup"><span data-stu-id="dbe20-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="dbe20-136">İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="dbe20-137">Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="dbe20-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="dbe20-138">Hizmet, dönüştürülmüş bir <xref:System.Uri.Host%2A?displayProperty=nameWithType> URI oluşturmak için, özellik değerini ve istek satırındaki dizeyi birleştirir. `http.sys`</span><span class="sxs-lookup"><span data-stu-id="dbe20-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="dbe20-139">Ayrıca, `http.sys` <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:</span><span class="sxs-lookup"><span data-stu-id="dbe20-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="dbe20-140">Tüm kodlanmış değerleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="dbe20-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="dbe20-141">Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dbe20-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="dbe20-142">UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dbe20-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="dbe20-143">Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.</span><span class="sxs-lookup"><span data-stu-id="dbe20-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="dbe20-144">İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="dbe20-145">Bu `http.sys` nedenle, işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:</span><span class="sxs-lookup"><span data-stu-id="dbe20-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="dbe20-146">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="dbe20-146">Registry Key</span></span>|<span data-ttu-id="dbe20-147">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="dbe20-147">Default Value</span></span>|<span data-ttu-id="dbe20-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbe20-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="dbe20-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="dbe20-149">EnableNonUTF8</span></span>|<span data-ttu-id="dbe20-150">1\.</span><span class="sxs-lookup"><span data-stu-id="dbe20-150">1</span></span>|<span data-ttu-id="dbe20-151">Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'leri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="dbe20-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="dbe20-152">Sıfır olmayan bir ise, `http.sys` isteklerde kodlanmış veya DBCS kodlu URL 'leri de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="dbe20-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="dbe20-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="dbe20-153">FavorUTF8</span></span>|<span data-ttu-id="dbe20-154">1\.</span><span class="sxs-lookup"><span data-stu-id="dbe20-154">1</span></span>|<span data-ttu-id="dbe20-155">Sıfır olmayan, `http.sys` her zaman UTF-8 olarak bir URL kodunu çözmeye çalışır; dönüştürme başarısız olursa ve EnableNonUTF8 sıfır değilse, http. sys bunu ANSI veya DBCS olarak çözmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="dbe20-156">Sıfır (ve EnableNonUTF8 sıfır olmayan) `http.sys` ise ANSI veya DBCS olarak kod çözmeye çalışır; bu başarılı olmazsa UTF-8 dönüşümü çalışır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="dbe20-157">Bir istek `http.sys` aldığında, dönüştürülmüş URI 'yi <xref:System.Net.HttpListenerRequest.Url%2A> özelliğe giriş olarak kullanır. <xref:System.Net.HttpListener></span><span class="sxs-lookup"><span data-stu-id="dbe20-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="dbe20-158">URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="dbe20-159">"1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="dbe20-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="dbe20-160">URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="dbe20-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="dbe20-161">Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="dbe20-162">Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:</span><span class="sxs-lookup"><span data-stu-id="dbe20-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="dbe20-163">Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="dbe20-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="dbe20-164">Bu, istek göndericisinin amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="dbe20-165">**UnescapeRequestUrl** özniteliği **false** <xref:System.Net.HttpListener> olarak ayarlanırsa, bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğe giriş `http.sys` olarak dönüştürülmüş URI yerine ham URI 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbe20-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="dbe20-166">**UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.</span><span class="sxs-lookup"><span data-stu-id="dbe20-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="dbe20-167">Özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir. <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A></span><span class="sxs-lookup"><span data-stu-id="dbe20-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbe20-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbe20-168">Example</span></span>  
 <span data-ttu-id="dbe20-169">Aşağıdaki örnek, <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine giriş `http.sys` olarak dönüştürülmüş URI yerine ham URI 'yi kullanmak için bir istek aldığında sınıfının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbe20-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="dbe20-170">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="dbe20-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="dbe20-171">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="dbe20-171">Namespace</span></span>|<span data-ttu-id="dbe20-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="dbe20-172">System.Net</span></span>|  
|<span data-ttu-id="dbe20-173">Şema adı</span><span class="sxs-lookup"><span data-stu-id="dbe20-173">Schema Name</span></span>||  
|<span data-ttu-id="dbe20-174">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="dbe20-174">Validation File</span></span>||  
|<span data-ttu-id="dbe20-175">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="dbe20-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="dbe20-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe20-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="dbe20-177">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="dbe20-177">Network Settings Schema</span></span>](index.md)
