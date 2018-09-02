---
title: Gelişmiş Biçim Seçimi
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: e5c396ce22e9021d453a70f3826b0bd3cc6aaf42
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466629"
---
# <a name="advanced-format-selection"></a>Gelişmiş Biçim Seçimi
Bu örnek, yeni giden yanıt biçimleri desteklemek için Windows Communication Foundation (WCF) REST programlama modeli genişletme gösterir. Ayrıca, örnek bir XHTML sayfası olarak gösteren bir görünüm stili programlama modeli nasıl uygulanabileceği yanıt döndürmek için T4 şablonu kullanır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Basit bir hizmet için hizmet isteği yapan istemci kodunun yanı sıra örnek oluşur.  Hizmet aşağıdaki yöntem imzasını olan tek bir [WebGet] işlem destekler: `Message EchoListWithGet(string list);`  
  
 İstemci hizmete istekte bulunduğunda öğelerinden virgülle ayrılmış bir listesini sağlar. `list` sorgu dizesi parametresi hizmet döndürür ve aynı listeleyen aşağıdaki biçimlerden birinde: XML, JSON, Atom, XHTML veya jpeg.  
  
 Hizmet tarafından döndürülen yanıt biçimi ilk tarafından belirlenen bir `format` sorgu dizesi parametresi ve istekle birlikte sağlanan bir HTTP kabul üstbilgisi tarafından saniye. Varsa değerini `format` sorgu dizesi parametresi, önceki biçimlerinden birini, ardından bu biçimde yanıt döndürülür. Varsa `format` sorgu dizesi mevcut olmaması durumunda hizmeti istek kabul etme üstbilgi öğeleri aracılığıyla yinelenir ve ilk içerik hizmetinin desteklediği türü biçimini döndürür.  
  
 İşlemin dönüş türü çarpmaktadır. Bir işlem dışında bir tür döndüren XML ve JSON yanıt formatları WCF REST programlama modeli yalnızca yerel olarak destekler <xref:System.ServiceModel.Channels.Message>. Ancak, kullanırken <xref:System.ServiceModel.Channels.Message> dönüş türü olarak Geliştirici iletisinin içeriği nasıl biçimlendirilmesi gerektiğini üzerinde tam denetime sahiptir.  
  
 Örnek kullanır <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> ve <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> dizeleri listesini XML, JSON ve ATOM iletilere sırasıyla serileştirmek için yöntemleri. Jpeg yanıt biçimi için <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> yöntemi kullanılır ve görüntünün akışa kaydedilir. XHTML yanıt <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> .tt dosyası ve bir otomatik olarak oluşturulan .cs dosyası oluşan Önişlenmiş T4 şablonu yanı sıra, kullanılır. .Tt dosyayı değişkenlerini içeren bir şablon biçimde yanıt yazın ve yapıları denetlemek bir geliştirici sağlar. T4 hakkında daha fazla bilgi için bkz: [oluşturma yapıları tarafından kullanarak metin şablonlarını](https://go.microsoft.com/fwlink/?LinkId=166023).  
  
 Örnek şirket içinde barındırılan bir hizmet ve içinde bir konsol uygulaması çalıştıran bir istemciyi oluşur. Konsol uygulamasının çalışır gibi istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Gelişmiş biçim seçimi için örnek çözümü açın. Başlatma sırasında [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde yürütmek için örnek için yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesine ve ardından **yönetici olarak çalıştır** bağlam menüsünden.  
  
2.  Çözümü derleyin ve konsol uygulaması AdvancedFormatSelection projesine hata ayıklama olmadan çalıştırmak için Ctrl-F5 tuşuna basın CTRL + SHIFT + B tuşlarına basın. Konsol penceresinde görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti.  
  
3.  Örnek çalışırken, istemci hizmete istekler gönderir ve konsol penceresine yanıtları yazar. Yanıtların farklı biçimler dikkat edin: XML, JSON, Atom ve XHTML.  
  
4.  Ardından, .jpeg biçimi yanıtta istek URI için Gözat istenir. Bir tarayıcı açın ve verilen URI için göz atın.  
  
5.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Ayrıca Bkz.
