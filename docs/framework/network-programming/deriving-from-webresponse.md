---
title: WebResponse’tan Türetme
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 6bdb21b8aaf8deb39e3abd68a69a9a5a10247e6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642951"
---
# <a name="deriving-from-webresponse"></a>WebResponse’tan Türetme
<xref:System.Net.WebResponse> .NET Framework takılabilir Protokolü modeli uygun bir protokole özgü yanıt oluşturmak için temel yöntemleri ve özellikleri sağlayan soyut bir temel sınıfı. Kullanan uygulamalar <xref:System.Net.WebRequest> istek verileri bir sınıfa kaynaklardan gelen yanıtları almak bir **WebResponse**. Protokole özgü **WebResponse** alt öğeleri, soyut üyelerini uygulanmalı **WebResponse** sınıfı.  
  
 İlişkili **WebRequest** sınıfı oluşturmalısınız **WebResponse** alt öğeleri. Örneğin, <xref:System.Net.HttpWebResponse> örnekleri yalnızca arama sonucu oluşturulan <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> veya <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Her **WebResponse** yüklenmek üzere tasarlanmamıştır ve bir kaynağa bir isteğinin sonucunu içerir.  
  
## <a name="contentlength-property"></a>ContentLength özelliğinin  
 <xref:System.Net.WebResponse.ContentLength%2A> Özelliği tarafından döndürülen akış kullanılabilir veri bayt sayısını gösterir <xref:System.Net.WebResponse.GetResponseStream%2A> yöntemi. **ContentLength** özelliği, üst bilgi veya meta veri bilgileri, sunucu tarafından döndürülen bayt sayısını gösteren değil; yalnızca İstenen kaynak verinin bayt sayısını gösterir.  
  
## <a name="contenttype-property"></a>ContentType özelliği  
 <xref:System.Net.WebResponse.ContentType%2A> Özelliği, protokol, sunucu tarafından gönderilen içerik türünü tanımlamak için istemciye gönderilecek gerektirdiği herhangi bir özel bilgiyi sağlar. Döndürülen verileri MIME içerik türü genellikle budur.  
  
## <a name="headers-property"></a>Üst özellik  
 <xref:System.Net.WebResponse.Headers%2A> Özelliği, rastgele bir ad/değer çiftleri Yanıtlı ilişkili meta verileri koleksiyonunu içerir. Ad/değer çifti eklenebilir olarak ifade edilebilir protokolü için gerekli tüm meta verilere **üstbilgileri** özelliği.  
  
 Kullanmak için gerekli **üstbilgileri** özelliğinin üstbilgi meta verileri kullanmak için. Protokole özgü meta veriler özellik olarak kullanıma sunulabilecek; Örneğin, <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> özelliği kullanıma sunan **son değiştirilme** HTTP üstbilgisi. Üst bilgi meta verilerini bir özellik olarak kullanıma sunduğunuzda, kullanarak ayarlamak aynı özellik vermemelidir **üstbilgileri** özelliği.  
  
## <a name="responseuri-property"></a>ResponseUri özelliği  
 <xref:System.Net.WebResponse.ResponseUri%2A> Özelliği gerçekten yanıtı verdi kaynağın URI'sini içerir. Yeniden yönlendirme, desteklemeyen protokoller için **ResponseUri** aynı olacaktır <xref:System.Net.WebRequest.RequestUri%2A> özelliği **WebRequest** yanıtı oluşturulur. İstek yönlendirme protokolü destekliyorsa, **ResponseUri** yanıt URI'sini içerir.  
  
## <a name="close-method"></a>Close Yöntemi  
 <xref:System.Net.WebResponse.Close%2A> Yöntemi istek ve yanıt tarafından yapılan tüm bağlantılar kapatır ve yanıt tarafından kullanılan kaynakları temizler. **Kapat** yöntemi yanıt tarafından kullanılan tüm stream örnekleri kapanır, ancak yanıt akışı yapılan bir çağrıyla daha önce kapalıysa bir özel durum oluşturmaz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="getresponsestream-method"></a>GetResponseStream yöntemi  
 <xref:System.Net.WebResponse.GetResponseStream%2A> Yöntem, istenen kaynak yanıtı içeren bir akış döndürür. Yanıt akışına yalnızca kaynak tarafından döndürülen veriler içerir. herhangi bir üst bilgi veya meta veriler yanıta dahil verilecek yanıtı çıkartılır ve uygulamaya protokole özgü özellikleri aracılığıyla sunulan veya **üstbilgileri** özelliği.  
  
 Tarafından döndürülen akış örneğini **GetResponseStream** yöntemi uygulama tarafından sahip olunan ve kapatmadan kapatılabilir **WebResponse**. Kural olarak, çağırma **WebResponse.Close** yöntemi tarafından döndürülen akış da kapatır **GetResponse yanıtına**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
- [WebRequest’ten Türetme](../../../docs/framework/network-programming/deriving-from-webrequest.md)
