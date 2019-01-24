---
title: '&lt;httpListener&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 896b6633ef4a741b9a7460d8ce3d879253d542da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577704"
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt; öğesi (ağ ayarları)
Tarafından kullanılan parametreler özelleştirir <xref:System.Net.HttpListener> sınıfı.  
  
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
|unescapeRequestUrl|Olmadığını gösteren bir Boole değeri bir <xref:System.Net.HttpListener> örneği yerine dönüştürülmüş URI ham atlanmayan URI kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 **UnescapeRequestUrl** özniteliği gösterir <xref:System.Net.HttpListener> ham atlanmayan URI burada herhangi bir yüzde olarak kodlanmış değerler dönüştürülür ve diğer normalleştirme adımları alınır dönüştürülmüş URI yerine kullanır.  
  
 Olduğunda bir <xref:System.Net.HttpListener> örneği bir talep aldığında `http.sys` hizmeti tarafından sağlanan URI dizesinin bir örneğini oluşturur `http.sys`ve olarak kullanıma sunduğu <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği.  
  
 `http.sys` Hizmetini iki istek URI dizelerini gösterir:  
  
-   Ham URI'si  
  
-   Dönüştürülen URI'si  
  
 Ham URI <xref:System.Uri?displayProperty=nameWithType> bir HTTP isteğinin istek satırında sağlanan:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Tarafından sağlanan ham URI `http.sys` , yukarıda belirtilen istek için "/ path /". Bu, HTTP fiili olarak ağ üzerinden gönderilen aşağıdaki dizeyi temsil eder.  
  
 `http.sys` Hizmeti HTTP isteği satırında sağlanan URI kullanılarak istekte sağlanan bilgileri dönüştürülen bir URI oluşturur ve kaynak sunucu isteği belirlemek için ana bilgisayar üstbilgisi iletilmesi. Bu bilgilerin istek kayıtlı URI ön ek kümesi ile karşılaştırarak gerçekleştirilir. HTTP sunucusu SDK Belgeleri HTTP_COOKED_URL yapısı olarak dönüştürülen bu URI'ye ifade eder.  
  
 Kayıtlı URI ön ekine sahip istek karşılaştırma mümkün olması için bazı normalleştirme isteğine yapılması gerekir. Dönüştürülen URI Yukarıdaki örnek şöyle olur:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` Hizmet birleştirir <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değeri ve dönüştürülen bir URI oluşturmak için istek satırı dizesini. Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı aynı zamanda şunları yapar:  
  
-   Geri Al çıkışları kodlanmış tüm yüzde değerleri.  
  
-   Yüzde olarak kodlanmış dönüştüren ASCII olmayan karakterler bir UTF-16 karakter temsili. UTF-8 ve ANSI/DBCS karakterlerin yanı sıra Unicode karakter (Unicode kodlama % uXXXX biçimini kullanarak) desteklendiğini unutmayın.  
  
-   Yol sıkıştırma gibi diğer normalleştirme adımları yürütür.  
  
 İstek değerlerini yüzde olarak kodlanmış kullanılan kodlama hakkında bilgi içermiyor olduğundan, doğru yüzde olarak kodlanmış değerler ayrıştırarak kodlama belirlemek mümkün olmayabilir.  
  
 Bu nedenle `http.sys` iki kayıt defteri anahtarlarını değiştirme işlemi sağlar:  
  
|Kayıt Defteri Anahtarı|Varsayılan Değer|Açıklama|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1.|Sıfır ise `http.sys` yalnızca UTF-8 olarak kodlanmış URL'ler kabul eder.<br /><br /> Sıfır olmayan, `http.sys` isteklerinde ANSI kodlu veya DBCS kodlu URL'leri de kabul eder.|  
|FavorUTF8|1.|Sıfır olmayan, `http.sys` bir URL UTF-8 ilk; bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır olmayan kod çözme için her zaman çalışır, Http.sys sonra ANSI veya DBCS olarak çözmeye çalışır.<br /><br /> Sıfır ise (ve EnableNonUTF8 sıfır olmayan), `http.sys` durumunda ANSI veya DBCS; olarak çözülmesi için deneme başarılı değil, UTF-8 dönüştürme çalışır.|  
  
 Zaman <xref:System.Net.HttpListener> bir istek alırsa dönüştürülmüş URI'SİNDEN kullanan `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.  
  
 Karakterler ve numaralar yanı sıra karakterleri Urılar içinde desteklemek için bir gereksinim yoktur. Müşteri için müşteri bilgilerini almak için kullanılan aşağıdaki URI örneğidir "1/3812" sayı:  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Yüzde olarak kodlanmış eğik çizgi (% 2F) uri'sindeki unutmayın. Bu durumda veri ve yol sınırlayıcısını eğik çizgi karakteri temsil ettiği bu gereklidir.  
  
 Dize URI oluşturucusuna geçirerek, aşağıdaki URI olmasına neden olur:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Yol segmentlerini bölme, aşağıdaki öğeleri neden olur:  
  
 `Customer('1`  
  
 `3812')`  
  
 Bu isteği gönderen amacı değildir.  
  
 Varsa **unescapeRequestUrl** özniteliği **false**, sonra ne zaman <xref:System.Net.HttpListener> bir istek alırsa yerine dönüştürülmüş URI'SİNDEN ham URI kullanan `http.sys` girişolarak<xref:System.Net.HttpListenerRequest.Url%2A> özelliği.  
  
 İçin varsayılan değer **unescapeRequestUrl** özniteliği **true**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Özelliği, geçerli değerini almak için kullanılabilir **unescapeRequestUrl** ilgili yapılandırma dosyaları özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.Net.HttpListener> sınıfı yerine dönüştürülmüş URI'SİNDEN ham URI kullanmak için bir istek aldığında `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.  
  
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
|Boş olabilir.||  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
