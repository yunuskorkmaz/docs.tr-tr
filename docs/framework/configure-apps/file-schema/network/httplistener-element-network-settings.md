---
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088385"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener > öğesi (ağ ayarları)
<xref:System.Net.HttpListener> sınıfı tarafından kullanılan parametreleri özelleştirir.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpListener >**

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
|unescapeRequestUrl 'Si|Bir <xref:System.Net.HttpListener> örneğinin, dönüştürülmüş URI yerine ham unatsız URI kullanıp kullanmadığını gösteren bir Boolean değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](settings-element-network-settings.md)|<xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 **UnescapeRequestUrl** özniteliği, <xref:System.Net.HttpListener> yüzde kodlamalı değerlerin dönüştürüldüğü ve diğer normalleştirme adımlarının alındığı dönüştürülmüş URI yerine ham unatsız URI 'yi kullanıp kullanmadığını belirtir.  
  
 Bir <xref:System.Net.HttpListener> örneği `http.sys` hizmeti üzerinden bir istek aldığında, `http.sys`tarafından sağlanmış URI dizesinin bir örneğini oluşturur ve bunu <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği olarak gösterir.  
  
 `http.sys` hizmeti iki istek URI dizesi kullanıma sunar:  
  
- Ham URI  
  
- Dönüştürülmüş URI  
  
 Ham URI, HTTP isteğinin istek satırında belirtilen <xref:System.Uri?displayProperty=nameWithType> ' dır:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Yukarıda bahsedilen istek için `http.sys` tarafından belirtilen ham URI, "/path/" dir. Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.  
  
 `http.sys` hizmeti, isteğin iletilmesi gereken kaynak sunucuyu belirleyebilmek için HTTP istek satırında ve ana bilgisayar üstbilgisinde belirtilen URI 'yi kullanarak istekte belirtilen bilgilerden dönüştürülmüş bir URI oluşturur. Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır. HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.  
  
 İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır. Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` hizmeti, dönüştürülmüş bir URI oluşturmak için <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değerini ve istek satırındaki dizeyi birleştirir. Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:  
  
- Tüm kodlanmış değerleri iptal eder.  
  
- Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür. UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.  
  
- Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.  
  
 İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.  
  
 Bu nedenle `http.sys` işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:  
  
|Kayıt Defteri Anahtarı|Varsayılan Değer|Açıklama|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1\.|Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'Leri kabul eder.<br /><br /> Sıfır olmayan `http.sys`, istekler içinde ANSI kodlamalı veya DBCS kodlu URL 'Leri de kabul eder.|  
|FavorUTF8|1\.|Sıfır olmayan `http.sys`, her zaman ilk olarak bir URL 'YI UTF-8 olarak çözmeye çalışır; Bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır olmayan bir değer ise, http. sys daha sonra ANSI veya DBCS olarak kodunu çözmeye çalışır.<br /><br /> Sıfır (ve EnableNonUTF8 sıfır olmayan) ise, `http.sys`, ANSI veya DBCS olarak kod çözmeye çalışır; Bu başarılı olmazsa, UTF-8 dönüşümü çalışır.|  
  
 <xref:System.Net.HttpListener> bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine girdi olarak `http.sys` dönüştürülmüş URI kullanır.  
  
 URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır. "1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin. Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.  
  
 Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:  
  
 `Customer('1`  
  
 `3812')`  
  
 Bu, istek göndericisinin amacı değildir.  
  
 **UnescapeRequestUrl** özniteliği **false**olarak ayarlandıysa <xref:System.Net.HttpListener> bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine GIRIŞ olarak `http.sys` dönüştürülmüş URI yerine ham URI kullanır.  
  
 **UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine girdi olarak `http.sys` dönüştürülmüş URI yerine ham URI kullanma isteği aldığında <xref:System.Net.HttpListener> sınıfının nasıl yapılandırılacağını gösterir.  
  
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
