---
description: "Hakkında daha fazla bilgi edinin: WebResponse 'dan türetme"
title: WebResponse’tan Türetme
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 5e941ce055091c6034640733465020ff62ce3721
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747484"
---
# <a name="deriving-from-webresponse"></a>WebResponse’tan Türetme

<xref:System.Net.WebResponse>Sınıfı, .NET Framework takılabilir protokol modeline uyan, protokole özgü bir yanıt oluşturmak için temel yöntemleri ve özellikleri sağlayan bir soyut temel sınıftır. <xref:System.Net.WebRequest>Kaynaklardan veri istemek için sınıfını kullanan uygulamalar, yanıtları bir **WebResponse** içinde alır. Protokole özgü **WebResponse** alt öğeleri, **WebResponse** sınıfının soyut üyelerini uygulamalıdır.  
  
 İlişkili **WebRequest** sınıfı **WebResponse** alt öğeleri oluşturmalıdır. Örneğin, <xref:System.Net.HttpWebResponse> örnekleri yalnızca veya çağırmanın sonucu olarak oluşturulur <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType> . Her **WebResponse** bir kaynağa yönelik isteğin sonucunu içerir ve yeniden kullanılması amaçlanmamıştır.  
  
## <a name="contentlength-property"></a>ContentLength özelliği  

 <xref:System.Net.WebResponse.ContentLength%2A>Özelliği, yöntemi tarafından döndürülen akıştan kullanılabilen veri baytlarının sayısını belirtir <xref:System.Net.WebResponse.GetResponseStream%2A> . **ContentLength** özelliği, sunucu tarafından döndürülen üst bilgi veya meta veri bilgisinin bayt sayısını göstermez; yalnızca istenen kaynaktaki verilerin bayt sayısını gösterir.  
  
## <a name="contenttype-property"></a>ContentType özelliği  

 <xref:System.Net.WebResponse.ContentType%2A>Özelliği, protokolizin sunucu tarafından gönderilen içeriğin türünü belirlemek üzere istemciye göndermenizi gerektiren özel bilgileri sağlar. Genellikle bu, döndürülen verilerin MIME içerik türüdür.  
  
## <a name="headers-property"></a>Headers özelliği  

 <xref:System.Net.WebResponse.Headers%2A>Özelliği, yanıtıyla ilişkili meta verilerin ad/değer çiftlerinin rastgele bir koleksiyonunu içerir. Protokol için gereken tüm meta **veriler, bir** ad/değer çifti olarak ifade edilebilir.  
  
 Üst bilgi meta verilerini kullanmak için **üstbilgiler** özelliğini kullanmanız gerekli değildir. Protokole özgü meta veriler, özellikler olarak gösterilebilir; Örneğin, özelliği, <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> **son değiştirilen** http üstbilgisini kullanıma sunar. Üst bilgi meta verilerini özellik olarak kullanıma sundığınızda, **üst bilgiler** özelliği kullanılarak aynı özelliğin belirtilmesine izin vermeniz gerekir.  
  
## <a name="responseuri-property"></a>ResponseUri özelliği  

 <xref:System.Net.WebResponse.ResponseUri%2A>Özelliği, yanıtı gerçekten sağlayan KAYNAĞıN URI 'sini içerir. Yeniden yönlendirmeyi desteklemeyen protokoller için **ResponseURI** , <xref:System.Net.WebRequest.RequestUri%2A> Yanıtı oluşturan **WebRequest** özelliği ile aynı olacaktır. Protokol isteği yeniden yönlendirmeyi destekliyorsa, **ResponseUri** yanıtın URI 'sini içerir.  
  
## <a name="close-method"></a>Close Yöntemi  

 <xref:System.Net.WebResponse.Close%2A>Yöntemi, istek ve yanıt tarafından yapılan tüm bağlantıları kapatır ve yanıt tarafından kullanılan kaynakları temizler. **Close** yöntemi, yanıt tarafından kullanılan tüm akış örneklerini kapatır, ancak yanıt akışı daha önce yönteme bir çağrı tarafından kapatılmışsa bir özel durum oluşturmaz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> .  
  
## <a name="getresponsestream-method"></a>GetResponseStream yöntemi  

 <xref:System.Net.WebResponse.GetResponseStream%2A>Yöntemi, istenen kaynaktaki yanıtı içeren bir akış döndürür. Yanıt akışı yalnızca kaynak tarafından döndürülen verileri içerir; yanıtta yer alan tüm üst bilgiler veya meta veriler yanıttan çıkarılır ve protokole özgü özellikler ya da **üstbilgiler** özelliği aracılığıyla uygulamaya sunulur.  
  
 **GetResponseStream** yöntemi tarafından döndürülen akış örneği uygulamaya aittir ve **WebResponse** kapatılmadan kapatılabilir. Kurala göre, **WebResponse. Close** yöntemini çağırmak **GetResponse** tarafından döndürülen akışı da kapatır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)
- [WebRequest’ten Türetme](deriving-from-webrequest.md)
