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
# <a name="httplistener-element-network-settings"></a>\<httpListener > öğesi (ağ ayarları)
<xref:System.Net.HttpListener> Sınıf tarafından kullanılan parametreleri özelleştirir.  
  
 \<Yapılandırma >  
\<system.net>  
\<Ayarlar >  
\<httpListener >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Tür  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|unescapeRequestUrl 'Si|Bir <xref:System.Net.HttpListener> Örneğin, dönüştürülmüş URI yerine ham unatsız URI kullanıp kullanmadığını gösteren bir Boolean değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](settings-element-network-settings.md)|<xref:System.Net> Ad alanı için temel ağ seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 **UnescapeRequestUrl** özniteliği, yüzde kodlamalı <xref:System.Net.HttpListener> değerlerin dönüştürüldüğü ve diğer normalleştirme adımlarının alındığı dönüştürülmüş URI yerine, ham kaçışsız URI kullanıp kullanmadığını belirtir.  
  
 Bir <xref:System.Net.HttpListener> örnek `http.sys` hizmet aracılığıyla bir istek aldığında, tarafından `http.sys`sağlanmış URI dizesinin bir örneğini oluşturur ve <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği olarak gösterir.  
  
 `http.sys` Hizmet iki istek URI dizesini kullanıma sunar:  
  
- Ham URI  
  
- Dönüştürülmüş URI  
  
 Ham URI <xref:System.Uri?displayProperty=nameWithType> , http isteğinin istek satırında verilmiştir:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Yukarıda belirtilen istek için tarafından `http.sys` belirtilen ham URI, "/path/" dir. Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.  
  
 `http.sys` Hizmet, isteğin iletilmesi gereken kaynak sunucuyu belirleyebilmek için http istek satırında ve ana bilgisayar üstbilgisinde belirtilen URI 'yi kullanarak istekte belirtilen bilgilerden dönüştürülmüş bir URI oluşturur. Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır. HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.  
  
 İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır. Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:  
  
 `http://www.contoso.com/path/`  
  
 Hizmet, dönüştürülmüş bir <xref:System.Uri.Host%2A?displayProperty=nameWithType> URI oluşturmak için, özellik değerini ve istek satırındaki dizeyi birleştirir. `http.sys` Ayrıca, `http.sys` <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:  
  
- Tüm kodlanmış değerleri iptal eder.  
  
- Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür. UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.  
  
- Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.  
  
 İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.  
  
 Bu `http.sys` nedenle, işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:  
  
|Kayıt Defteri Anahtarı|Varsayılan Değer|Açıklama|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1\.|Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'leri kabul eder.<br /><br /> Sıfır olmayan bir ise, `http.sys` isteklerde kodlanmış veya DBCS kodlu URL 'leri de kabul eder.|  
|FavorUTF8|1\.|Sıfır olmayan, `http.sys` her zaman UTF-8 olarak bir URL kodunu çözmeye çalışır; dönüştürme başarısız olursa ve EnableNonUTF8 sıfır değilse, http. sys bunu ANSI veya DBCS olarak çözmeye çalışır.<br /><br /> Sıfır (ve EnableNonUTF8 sıfır olmayan) `http.sys` ise ANSI veya DBCS olarak kod çözmeye çalışır; bu başarılı olmazsa UTF-8 dönüşümü çalışır.|  
  
 Bir istek `http.sys` aldığında, dönüştürülmüş URI 'yi <xref:System.Net.HttpListenerRequest.Url%2A> özelliğe giriş olarak kullanır. <xref:System.Net.HttpListener>  
  
 URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır. "1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin. Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.  
  
 Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:  
  
 `Customer('1`  
  
 `3812')`  
  
 Bu, istek göndericisinin amacı değildir.  
  
 **UnescapeRequestUrl** özniteliği **false** <xref:System.Net.HttpListener> olarak ayarlanırsa, bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğe giriş `http.sys` olarak dönüştürülmüş URI yerine ham URI 'yi kullanır.  
  
 **UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.  
  
 Özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir. <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine giriş `http.sys` olarak dönüştürülmüş URI yerine ham URI 'yi kullanmak için bir istek aldığında sınıfının nasıl yapılandırılacağını gösterir.  
  
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
  
## <a name="element-information"></a>Öğe Bilgisi  
  
|||
|-|-|  
|Ad Alanı|System.Net|  
|Şema adı||  
|Doğrulama dosyası||  
|Boş olabilir||  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Ağ Ayarları Şeması](index.md)
