---
title: WebResponse’tan Türetme
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: bd06928b08eb085ef13371687fb1e5b92c6c1d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048577"
---
# <a name="deriving-from-webresponse"></a>WebResponse’tan Türetme
Sınıf, <xref:System.Net.WebResponse> .NET Framework takılabilir protokol modeline uyan protokole özgü bir yanıt oluşturmak için temel yöntemleri ve özellikleri sağlayan soyut bir taban sınıfıdır. Kaynaklardan veri <xref:System.Net.WebRequest> istemek için sınıfı kullanan uygulamalar yanıtları bir **WebResponse'da**alır. Protokole özgü **WebResponse** **torunları, WebResponse** sınıfının soyut üyelerini uygulamalıdır.  
  
 İlişkili **Webİstek** **sınıfı, WebResponse** torunlarını oluşturmalıdır. Örneğin, <xref:System.Net.HttpWebResponse> örnekler yalnızca arama <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> veya <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>. Her **WebResponse** bir kaynağa yapılan bir isteğin sonucunu içerir ve yeniden kullanılması amaçlanmamıştır.  
  
## <a name="contentlength-property"></a>İçerik Uzunluğu Özelliği  
 Özellik, <xref:System.Net.WebResponse.ContentLength%2A> <xref:System.Net.WebResponse.GetResponseStream%2A> yöntem tarafından döndürülen akıştan kullanılabilen bayt veri sayısını gösterir. **ContentLength** özelliği, sunucu tarafından döndürülen üstbilgi veya meta veri bilgilerinin bayt sayısını göstermez; yalnızca istenen kaynağın kendisindeki bayt veri sayısını gösterir.  
  
## <a name="contenttype-property"></a>İçerikTürü Özelliği  
 Özellik, <xref:System.Net.WebResponse.ContentType%2A> protokolünüzün sunucu tarafından gönderilen içerik türünü belirlemek için istemciye göndermenizi gerektirdiği özel bilgileri sağlar. Genellikle bu, döndürülen herhangi bir verinin MIME içerik türüdür.  
  
## <a name="headers-property"></a>Üstbilgi Özelliği  
 Özellik, <xref:System.Net.WebResponse.Headers%2A> yanıtla ilişkili meta verilerin ad/değer çiftleri rasgele bir koleksiyon içerir. Protokol tarafından ad/değer çifti olarak ifade edilebilen meta veriler **Üstbilgi** özelliğine dahil edilebilir.  
  
 Üstbilgi meta verilerini kullanmak için **Üstbilgiler** özelliğini kullanmanız gerekmez. Protokole özgü meta veriler özellik olarak ortaya çıkabilir; örneğin, <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> özellik **Son Değiştirilen** HTTP üstbilgisini ortaya çıkarır. Üstbilgi meta verilerini bir özellik olarak ortaya çıkarırken, aynı özelliğin **Üstbilgi** özelliğikullanılarak ayarlanabilmesine izin vermemelisiniz.  
  
## <a name="responseuri-property"></a>Responseuri Özelliği  
 Özellik, <xref:System.Net.WebResponse.ResponseUri%2A> yanıtı gerçekten sağlayan kaynağın URI'sini içerir. Yeniden yönlendirmeyi desteklemeyen protokoller için **ResponseUri,** yanıtı <xref:System.Net.WebRequest.RequestUri%2A> oluşturan **WebRequest'in** özelliğiyle aynı olacaktır. Protokol isteğin yeniden yönlendirilmesine destek verirse, **ResponseUri** yanıtın URI'sini içerir.  
  
## <a name="close-method"></a>Close Yöntemi  
 Yöntem, <xref:System.Net.WebResponse.Close%2A> istek ve yanıt tarafından yapılan bağlantıları kapatır ve yanıt tarafından kullanılan kaynakları temizler. Yanıt tarafından kullanılan tüm akış örneklerini **kapatan Kapat** yöntemi, yanıt akışı daha önce <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yönteme yapılan bir çağrı yla kapatılmışsa özel durum atmaz.  
  
## <a name="getresponsestream-method"></a>GetResponseStream Yöntemi  
 Yöntem, <xref:System.Net.WebResponse.GetResponseStream%2A> istenen kaynaktan gelen yanıtı içeren bir akış döndürür. Yanıt akışı yalnızca kaynak tarafından döndürülen verileri içerir; yanıtta yer alan herhangi bir üstbilgi veya meta veri yanıttan çıkarılmalı ve protokole özgü özellikler veya **Üstbilgiler** özelliği aracılığıyla uygulamaya maruz kalmalıdır.  
  
 **GetResponseStream** yöntemi tarafından döndürülen akış örneği uygulamaya aittir ve **WebResponse'u**kapatmadan kapatılabilir. Sözleşmeye göre, **WebResponse.Close** yöntemini arayarak **GetResponse**tarafından döndürülen akışı da kapatır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)
- [WebRequest’ten Türetme](deriving-from-webrequest.md)
