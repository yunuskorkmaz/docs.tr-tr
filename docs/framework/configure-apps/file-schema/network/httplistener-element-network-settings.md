---
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 3f75096681ab07dd6d4788fbded5ca5c4a024aef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698190"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener > öğesi (ağ ayarları)
@No__t-0 sınıfı tarafından kullanılan parametreleri özelleştirir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<httpListener >**  
  
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
|[Ayarlar](settings-element-network-settings.md)|@No__t-0 ad alanı için temel ağ seçeneklerini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 **UnescapeRequestUrl** özniteliği, <xref:System.Net.HttpListener> ' in, yüzde kodlamalı değerlerin dönüştürüldüğü ve diğer normalleştirme adımlarının alındığı dönüştürülmüş URI yerine, ham unatsız URI kullanıp kullanmadığını belirtir.  
  
 @No__t-0 örneği `http.sys` hizmeti üzerinden bir istek aldığında, `http.sys` tarafından sağlanmış URI dizesinin bir örneğini oluşturur ve bunu <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği olarak gösterir.  
  
 @No__t-0 hizmeti iki istek URI dizesini kullanıma sunar:  
  
- Ham URI  
  
- Dönüştürülmüş URI  
  
 Ham URI, HTTP isteğinin istek satırında belirtilen <xref:System.Uri?displayProperty=nameWithType> ' dır:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Yukarıda bahsedilen istek için `http.sys` tarafından belirtilen ham URI, "/path/" dir. Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.  
  
 @No__t-0 hizmeti, HTTP istek satırında belirtilen URI 'yi ve isteğin iletilmesi gereken kaynak sunucuyu belirleme ana bilgisayar üst bilgisini kullanarak istekte belirtilen bilgilerden dönüştürülmüş bir URI oluşturur. Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır. HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.  
  
 İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır. Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:  
  
 `http://www.contoso.com/path/`  
  
 @No__t-0 hizmeti, dönüştürülmüş bir URI oluşturmak için <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değerini ve istek satırındaki dizeyi birleştirir. Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:  
  
- Tüm kodlanmış değerleri iptal eder.  
  
- Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür. UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.  
  
- Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.  
  
 İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.  
  
 Bu nedenle `http.sys` işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:  
  
|Kayıt Defteri Anahtarı|Varsayılan Değer|Açıklama|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1\.|Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'Leri kabul eder.<br /><br /> Sıfır olmayan `http.sys`, istekler içinde ANSI kodlamalı veya DBCS kodlu URL 'Leri de kabul eder.|  
|FavorUTF8|1\.|Sıfır olmayan `http.sys`, her zaman ilk olarak bir URL 'YI UTF-8 olarak çözmeye çalışır; Bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır olmayan bir değer ise, http. sys daha sonra ANSI veya DBCS olarak kodunu çözmeye çalışır.<br /><br /> Sıfır (ve EnableNonUTF8 sıfır olmayan) ise, `http.sys`, ANSI veya DBCS olarak kod çözmeye çalışır; Bu başarılı olmazsa, UTF-8 dönüşümü çalışır.|  
  
 @No__t-0 bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine giriş olarak `http.sys` ' den dönüştürülmüş URI kullanır.  
  
 URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır. "1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin. Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.  
  
 Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:  
  
 `Customer('1`  
  
 `3812')`  
  
 Bu, istek göndericisinin amacı değildir.  
  
 **UnescapeRequestUrl** özniteliği **false**olarak ayarlanırsa, <xref:System.Net.HttpListener> bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine giriş olarak `http.sys` ' ten dönüştürülmüş URI yerine ham URI 'yi kullanır.  
  
 **UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.  
  
 @No__t-0 özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine giriş olarak `http.sys` ' den dönüştürülen URI yerine ham URI 'yi kullanmak için bir istek aldığında <xref:System.Net.HttpListener> sınıfının nasıl yapılandırılacağını gösterir.  
  
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
