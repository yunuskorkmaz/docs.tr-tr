---
title: '&lt;httpListener&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a327f757f26c815d5b2cffe179af68bbe3d152eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744882"
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
|unescapeRequestUrl|Olmadığını gösteren bir Boole değeri bir <xref:System.Net.HttpListener> örneği yerine dönüştürülen URI ham atlanmayan URI kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[Ayarlar](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Temel ağ seçeneklerini yapılandırır <xref:System.Net> ad alanı.|  
  
## <a name="remarks"></a>Açıklamalar  
 **UnescapeRequestUrl** öznitelik gösterir <xref:System.Net.HttpListener> ham atlanmayan URI burada tüm yüzde olarak kodlanmış değerler dönüştürülür ve diğer normalleştirme adımları gerçekleştirilecek dönüştürülen URI yerine kullanır.  
  
 Zaman bir <xref:System.Net.HttpListener> örneği üzerinden bir istek aldığında `http.sys` hizmeti tarafından sağlanan URI dizesinin bir örneğini oluşturur `http.sys`ve olarak ortaya çıkaran <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği.  
  
 `http.sys` Hizmet sunan iki istek URI dizelerini:  
  
-   Ham URI  
  
-   Dönüştürülen URI  
  
 Ham URI <xref:System.Uri?displayProperty=nameWithType> bir HTTP isteği isteği satırına:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Tarafından sağlanan ham URI `http.sys` , yukarıda belirtilen istek için "/ yol /". Bu ağ üzerinden gönderildiği gibi HTTP fiili aşağıdaki dizeyi temsil eder.  
  
 `http.sys` Hizmeti HTTP isteği satırında sağlanan URI kullanılarak isteğinde sağlanan bilgilerden dönüştürülen bir URI oluşturur ve kaynak sunucu isteği belirlemek için ana bilgisayar üstbilgisi iletilmesi gereken. Bu bilgilerin istek kayıtlı URI ön ek kümesi ile karşılaştırarak gerçekleştirilir. HTTP sunucusu SDK Belgeleri dönüştürülen bu URI HTTP_COOKED_URL yapısı olarak ifade eder.  
  
 Kayıtlı URI önekleri istekle karşılaştırmak oluşturabilmek, istek için bazı normalleştirme yapılmalıdır. Dönüştürülen URI Yukarıdaki örnek için aşağıdaki gibi olur:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys` Hizmet birleştirir <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değeri ve dönüştürülen bir URI oluşturmak için istek satırdaki dize. Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı ayrıca aşağıdakileri yapar:  
  
-   Kaydını çıkışları kodlanmış tüm yüzde değerleri.  
  
-   ASCII olmayan karakterlere UTF-16 karakter gösterimi yüzde olarak kodlanmış dönüştürür. UTF-8 ile ANSI/DBCS karakter (% uXXXX biçimini kullanarak Unicode kodlama) Unicode karakterler yanı sıra desteklendiğini unutmayın.  
  
-   Yol sıkıştırma gibi diğer normalleştirme adımları yürütür.  
  
 Yüzde olarak kodlanmış değerler için kullanılan kodlamayı hakkında bilgi içermiyor. istek olduğundan, doğru yüzde olarak kodlanmış değerlerin ayrıştırarak kodlama belirlemek mümkün olmayabilir.  
  
 Bu nedenle `http.sys` işlemi değiştirmek için iki kayıt defteri anahtarlarını sağlar:  
  
|Kayıt Defteri Anahtarı|Varsayılan Değer|Açıklama|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1.|Sıfır ise, `http.sys` yalnızca UTF-8 olarak kodlanmış URL'leri kabul eder.<br /><br /> Sıfır olursa, `http.sys` de ANSI ile kodlanmış veya DBCS kodlanmış URL'leri istekleri kabul eder.|  
|FavorUTF8|1.|Sıfır olursa, `http.sys` bir URL UTF-8 olarak ilk; bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır kodunu çözmek için her zaman çalışır, Http.sys sonra ANSI veya DBCS olarak çözmeye çalışır.<br /><br /> Sıfır ise (ve EnableNonUTF8 sıfır olmayan), `http.sys` o varsa ANSI veya DBCS; olarak çözülmesi için deneme başarılı değil, UTF-8 dönüştürme çalışır.|  
  
 Zaman <xref:System.Net.HttpListener> bir istek alırsa dönüştürülen URI'den kullanan `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.  
  
 Karakterleri karakter ve sayıları yanı sıra içinde URI'ler desteklemek için gereksinim yoktur. Müşteri için müşteri bilgilerini almak için kullanılan aşağıdaki URI örneğidir sayı "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Yüzde olarak kodlanmış eğik çizgi (% 2F) URI unutmayın. Bu durumda veriler ve bir yol ayırıcısı eğik çizgi karakteri temsil ettiği bu gereklidir.  
  
 Dize URI oluşturucusuna geçirerek, aşağıdaki URI olmasına neden olur:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Yolun kendi kesimler halinde bölme aşağıdaki öğeleri neden olur:  
  
 `Customer('1`  
  
 `3812')`  
  
 Bu isteği gönderen amacı değildir.  
  
 Varsa **unescapeRequestUrl** özniteliği olarak ayarlanmış **false**, sonra ne zaman <xref:System.Net.HttpListener> bir istek alırsa dönüştürülen URI'den yerine ham URI kullanan `http.sys` girişolarak<xref:System.Net.HttpListenerRequest.Url%2A> özelliği.  
  
 İçin varsayılan değer **unescapeRequestUrl** özniteliği **doğru**.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Özelliği, geçerli değerini almak için kullanılabilir **unescapeRequestUrl** geçerli yapılandırma dosyalarını özniteliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl yapılandırılacağını gösterir <xref:System.Net.HttpListener> sınıfı yerine dönüştürülmüş URI'SİNDEN ham URI kullanmak için bir istek aldığında `http.sys` giriş olarak <xref:System.Net.HttpListenerRequest.Url%2A> özelliği.  
  
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
|Dosya doğrulama||  
|Boş olabilir.||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
