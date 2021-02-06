---
description: 'Daha fazla bilgi edinin: <httpListener> öğesi (ağ ayarları)'
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 18c139ad7767370ecd3a4116e352b7614914d199
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652867"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="52914-103">\<httpListener> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="52914-103">\<httpListener> Element (Network Settings)</span></span>

<span data-ttu-id="52914-104">Sınıf tarafından kullanılan parametreleri özelleştirir <xref:System.Net.HttpListener> .</span><span class="sxs-lookup"><span data-stu-id="52914-104">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="52914-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="52914-105">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="52914-106">Tür</span><span class="sxs-lookup"><span data-stu-id="52914-106">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52914-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52914-107">Attributes and Elements</span></span>  

 <span data-ttu-id="52914-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52914-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52914-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52914-109">Attributes</span></span>  
  
|<span data-ttu-id="52914-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52914-110">Attribute</span></span>|<span data-ttu-id="52914-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52914-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52914-112">unescapeRequestUrl 'Si</span><span class="sxs-lookup"><span data-stu-id="52914-112">unescapeRequestUrl</span></span>|<span data-ttu-id="52914-113">Bir <xref:System.Net.HttpListener> Örneğin, dönüştürülmüş URI yerine ham unatsız URI kullanıp kullanmadığını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="52914-113">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52914-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52914-114">Child Elements</span></span>  

 <span data-ttu-id="52914-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="52914-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52914-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52914-116">Parent Elements</span></span>  
  
|<span data-ttu-id="52914-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="52914-117">**Element**</span></span>|<span data-ttu-id="52914-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="52914-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="52914-119">ayarlar</span><span class="sxs-lookup"><span data-stu-id="52914-119">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="52914-120">Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="52914-120">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52914-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52914-121">Remarks</span></span>  

 <span data-ttu-id="52914-122">**UnescapeRequestUrl** özniteliği, <xref:System.Net.HttpListener> yüzde kodlamalı değerlerin dönüştürüldüğü ve diğer normalleştirme ADıMLARıNıN alındığı dönüştürülmüş URI yerine, ham kaçışsız URI kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="52914-122">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="52914-123">Bir <xref:System.Net.HttpListener> örnek hizmet aracılığıyla bir istek aldığında `http.sys` , tarafından sağlanmış URI dizesinin bir örneğini oluşturur `http.sys` ve özelliği olarak gösterir <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="52914-123">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="52914-124">`http.sys`Hizmet iki Istek URI dizesini kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="52914-124">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="52914-125">Ham URI</span><span class="sxs-lookup"><span data-stu-id="52914-125">Raw URI</span></span>  
  
- <span data-ttu-id="52914-126">Dönüştürülmüş URI</span><span class="sxs-lookup"><span data-stu-id="52914-126">Converted URI</span></span>  
  
 <span data-ttu-id="52914-127">Ham URI, <xref:System.Uri?displayProperty=nameWithType> http isteğinin istek satırında verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="52914-127">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="52914-128">Yukarıda belirtilen istek için tarafından belirtilen ham URI, `http.sys` "/path/" dir.</span><span class="sxs-lookup"><span data-stu-id="52914-128">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="52914-129">Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52914-129">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="52914-130">Hizmet, isteğin `http.sys` iletilmesi gereken kaynak sunucuyu belirleyebilmek IÇIN http istek satırında ve ana bilgisayar üstbilgisinde BELIRTILEN URI 'yi kullanarak istekte belirtilen bilgilerden dönüştürülmüş BIR URI oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52914-130">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="52914-131">Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="52914-131">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="52914-132">HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.</span><span class="sxs-lookup"><span data-stu-id="52914-132">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="52914-133">İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52914-133">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="52914-134">Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="52914-134">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="52914-135">`http.sys`Hizmet, <xref:System.Uri.Host%2A?displayProperty=nameWithType> dönüştürülmüş bir URI oluşturmak için, özellik değerini ve istek satırındaki dizeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="52914-135">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="52914-136">Ayrıca, `http.sys` <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:</span><span class="sxs-lookup"><span data-stu-id="52914-136">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="52914-137">Tüm kodlanmış değerleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="52914-137">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="52914-138">Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="52914-138">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="52914-139">UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="52914-139">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="52914-140">Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.</span><span class="sxs-lookup"><span data-stu-id="52914-140">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="52914-141">İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="52914-141">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="52914-142">Bu nedenle `http.sys` , işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:</span><span class="sxs-lookup"><span data-stu-id="52914-142">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="52914-143">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="52914-143">Registry Key</span></span>|<span data-ttu-id="52914-144">Varsayılan değer</span><span class="sxs-lookup"><span data-stu-id="52914-144">Default Value</span></span>|<span data-ttu-id="52914-145">Description</span><span class="sxs-lookup"><span data-stu-id="52914-145">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="52914-146">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="52914-146">EnableNonUTF8</span></span>|<span data-ttu-id="52914-147">1</span><span class="sxs-lookup"><span data-stu-id="52914-147">1</span></span>|<span data-ttu-id="52914-148">Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'leri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="52914-148">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="52914-149">Sıfır olmayan bir ise, `http.sys` isteklerde kodlanmış veya DBCS kodlu URL 'leri de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="52914-149">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="52914-150">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="52914-150">FavorUTF8</span></span>|<span data-ttu-id="52914-151">1</span><span class="sxs-lookup"><span data-stu-id="52914-151">1</span></span>|<span data-ttu-id="52914-152">Sıfır olmayan, `http.sys` her zaman UTF-8 olarak BIR URL kodunu çözmeye çalışır; dönüştürme başarısız olursa ve EnableNonUTF8 sıfır değilse, Http.sys ANSI veya DBCS olarak kod çözmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="52914-152">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="52914-153">Sıfır (ve EnableNonUTF8 sıfır olmayan) ise `http.sys` ANSI veya DBCS olarak kod çözmeye çalışır; bu başarılı olmazsa UTF-8 dönüşümü çalışır.</span><span class="sxs-lookup"><span data-stu-id="52914-153">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="52914-154"><xref:System.Net.HttpListener>Bir istek aldığında, dönüştürülmüş URI 'yi `http.sys` özelliğe giriş olarak kullanır <xref:System.Net.HttpListenerRequest.Url%2A> .</span><span class="sxs-lookup"><span data-stu-id="52914-154">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="52914-155">URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır.</span><span class="sxs-lookup"><span data-stu-id="52914-155">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="52914-156">"1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="52914-156">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="52914-157">URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="52914-157">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="52914-158">Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="52914-158">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="52914-159">Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:</span><span class="sxs-lookup"><span data-stu-id="52914-159">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="52914-160">Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="52914-160">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="52914-161">Bu, istek göndericisinin amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="52914-161">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="52914-162">**UnescapeRequestUrl** özniteliği **false** olarak ayarlanırsa, <xref:System.Net.HttpListener> bir istek aldığında, `http.sys` özelliğe GIRIŞ olarak dönüştürülmüş URI yerine ham URI 'yi kullanır <xref:System.Net.HttpListenerRequest.Url%2A> .</span><span class="sxs-lookup"><span data-stu-id="52914-162">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="52914-163">**UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.</span><span class="sxs-lookup"><span data-stu-id="52914-163">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="52914-164"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>Özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52914-164">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52914-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="52914-165">Example</span></span>  

 <span data-ttu-id="52914-166">Aşağıdaki örnek, <xref:System.Net.HttpListener> özelliğine giriş olarak dönüştürülmüş URI yerine ham URI 'yi kullanmak için bir istek aldığında sınıfının nasıl yapılandırılacağını gösterir `http.sys` <xref:System.Net.HttpListenerRequest.Url%2A> .</span><span class="sxs-lookup"><span data-stu-id="52914-166">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="52914-167">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="52914-167">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="52914-168">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="52914-168">Namespace</span></span>|<span data-ttu-id="52914-169">System.Net</span><span class="sxs-lookup"><span data-stu-id="52914-169">System.Net</span></span>|  
|<span data-ttu-id="52914-170">Şema adı</span><span class="sxs-lookup"><span data-stu-id="52914-170">Schema Name</span></span>||  
|<span data-ttu-id="52914-171">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="52914-171">Validation File</span></span>||  
|<span data-ttu-id="52914-172">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="52914-172">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="52914-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52914-173">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="52914-174">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="52914-174">Network Settings Schema</span></span>](index.md)
