---
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 78526559164939667eab8848bc5fd2af6749d474
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195447"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener> Öğesi (Ağ Ayarları)

Sınıf tarafından kullanılan parametreleri özelleştirir <xref:System.Net.HttpListener> .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a>Syntax  
  
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
  
|**Dosyalarında**|**Açıklama**|  
|-----------------|---------------------|  
|[ayarlar](settings-element-network-settings.md)|Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net> .|  
  
## <a name="remarks"></a>Açıklamalar  

 **UnescapeRequestUrl** özniteliği, <xref:System.Net.HttpListener> yüzde kodlamalı değerlerin dönüştürüldüğü ve diğer normalleştirme ADıMLARıNıN alındığı dönüştürülmüş URI yerine, ham kaçışsız URI kullanıp kullanmadığını belirtir.  
  
 Bir <xref:System.Net.HttpListener> örnek hizmet aracılığıyla bir istek aldığında `http.sys` , tarafından sağlanmış URI dizesinin bir örneğini oluşturur `http.sys` ve özelliği olarak gösterir <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> .  
  
 `http.sys`Hizmet iki Istek URI dizesini kullanıma sunar:  
  
- Ham URI  
  
- Dönüştürülmüş URI  
  
 Ham URI, <xref:System.Uri?displayProperty=nameWithType> http isteğinin istek satırında verilmiştir:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 Yukarıda belirtilen istek için tarafından belirtilen ham URI, `http.sys` "/path/" dir. Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.  
  
 Hizmet, isteğin `http.sys` iletilmesi gereken kaynak sunucuyu belirleyebilmek IÇIN http istek satırında ve ana bilgisayar üstbilgisinde BELIRTILEN URI 'yi kullanarak istekte belirtilen bilgilerden dönüştürülmüş BIR URI oluşturur. Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır. HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.  
  
 İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır. Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:  
  
 `http://www.contoso.com/path/`  
  
 `http.sys`Hizmet, <xref:System.Uri.Host%2A?displayProperty=nameWithType> dönüştürülmüş bir URI oluşturmak için, özellik değerini ve istek satırındaki dizeyi birleştirir. Ayrıca, `http.sys` <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:  
  
- Tüm kodlanmış değerleri iptal eder.  
  
- Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür. UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.  
  
- Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.  
  
 İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.  
  
 Bu nedenle `http.sys` , işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:  
  
|Kayıt Defteri Anahtarı|Varsayılan değer|Açıklama|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'leri kabul eder.<br /><br /> Sıfır olmayan bir ise, `http.sys` isteklerde kodlanmış veya DBCS kodlu URL 'leri de kabul eder.|  
|FavorUTF8|1|Sıfır olmayan, `http.sys` her zaman UTF-8 olarak BIR URL kodunu çözmeye çalışır; dönüştürme başarısız olursa ve EnableNonUTF8 sıfır değilse, Http.sys ANSI veya DBCS olarak kod çözmeye çalışır.<br /><br /> Sıfır (ve EnableNonUTF8 sıfır olmayan) ise `http.sys` ANSI veya DBCS olarak kod çözmeye çalışır; bu başarılı olmazsa UTF-8 dönüşümü çalışır.|  
  
 <xref:System.Net.HttpListener>Bir istek aldığında, dönüştürülmüş URI 'yi `http.sys` özelliğe giriş olarak kullanır <xref:System.Net.HttpListenerRequest.Url%2A> .  
  
 URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır. "1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin. Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.  
  
 Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:  
  
 `Customer('1`  
  
 `3812')`  
  
 Bu, istek göndericisinin amacı değildir.  
  
 **UnescapeRequestUrl** özniteliği **false**olarak ayarlanırsa, <xref:System.Net.HttpListener> bir istek aldığında, `http.sys` özelliğe GIRIŞ olarak dönüştürülmüş URI yerine ham URI 'yi kullanır <xref:System.Net.HttpListenerRequest.Url%2A> .  
  
 **UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.  
  
 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>Özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Net.HttpListener> özelliğine giriş olarak dönüştürülmüş URI yerine ham URI 'yi kullanmak için bir istek aldığında sınıfının nasıl yapılandırılacağını gösterir `http.sys` <xref:System.Net.HttpListenerRequest.Url%2A> .  
  
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
- [Ağ ayarları şeması](index.md)
