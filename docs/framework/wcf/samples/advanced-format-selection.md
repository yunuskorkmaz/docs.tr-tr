---
title: Gelişmiş Biçim Seçimi
ms.date: 03/30/2017
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
ms.openlocfilehash: 4913d8dbf69f574aa4f329279bed0d92710512f9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="advanced-format-selection"></a>Gelişmiş Biçim Seçimi
Bu örnek, yeni giden yanıt formatları desteklemek için Windows Communication Foundation (WCF) REST programlama modelini gösterilmiştir. Ayrıca, örnek bir görünüm stili programlama modeli nasıl uygulanabilir gösteren bir XHTML sayfası olarak yanıt dönmesini T4 şablon kullanır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Örnek hizmete istek yaptığında istemci kodu ile birlikte basit bir servis oluşur.  Hizmeti, aşağıdaki yöntemi imzası olan tek bir [WebGet] işlemi destekler: `Message EchoListWithGet(string list);`  
  
 İstemci hizmete istekte bulunduğunda öğelerinden virgülle ayrılmış bir listesini sağlar `list` sorgu dizesi parametresi hizmet döndürür ve aynı listeleyen aşağıdaki biçimlerden birinde: XML, JSON, Atom, XHTML veya jpeg.  
  
 Hizmet tarafından döndürülen yanıt biçimi öncelikle tarafından belirlenen bir `format` sorgu dizesi parametresi ve ikinci isteği ile sağlanan bir HTTP kabul üstbilgisi tarafından. Varsa değerini `format` sorgu dizesi parametresidir önceki biçimlerinden birini ve ardından o biçiminde bir yanıt döndürdü. Varsa `format` sorgu dizesi mevcut değil ve hizmet isteği kabul etme üstbilgi öğeleri dolaşır ve ilk içerik hizmetini destekleyen türü biçimini döndürür.  
  
 Dönüş işlemi belirtmeye değer türüdür. Bir işlem başka bir tür döndüren XML ve JSON yanıt formatları WCF REST programlama modeli yalnızca yerel olarak destekler <xref:System.ServiceModel.Channels.Message>. Ancak, kullanırken <xref:System.ServiceModel.Channels.Message> dönüş türü olarak Geliştirici iletinin içeriğinin nasıl biçimlendirilmiş üzerinde tam denetim sahiptir.  
  
 Örnek kullanır <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> ve <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> dizelerin listesi XML, JSON ve ATOM iletilere sırasıyla serileştirmek için yöntemleri. Jpeg yanıt biçimi için <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> yöntemi kullanılır ve görüntü akışa kaydedilir. XHTML yanıt <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> .tt dosyası ve bir otomatik olarak oluşturulan .cs dosyası oluşan bir önceden işlenmiş T4 şablon ile birlikte kullanılır. .Tt dosya değişkenlerini içeren bir şablon biçiminde bir yanıt yazma ve yapıları denetlemek bir geliştirici sağlar. T4 hakkında daha fazla bilgi için bkz: [oluşturma yapıları tarafından kullanarak metin şablonlarını](http://go.microsoft.com/fwlink/?LinkId=166023).  
  
 Kendini barındıran hizmet ve bir konsol uygulaması içinde çalıştırılan bir istemciyi, örnek oluşur. Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Gelişmiş biçim seçimi için örnek çözümü açın. Başlatılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde çalıştırmak için örnek yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesi ve seçme **yönetici olarak çalıştır** ve bağlam menüsünden.  
  
2.  Çözümü derlemek ve hata ayıklama olmadan konsol uygulaması AdvancedFormatSelection projesini çalıştırmak için Ctrl-F5 tuşuna basın CTRL + SHIFT + B tuşuna basın. Konsol penceresinde görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur.  
  
3.  Örnek çalışırken, istemci istekleri hizmetine gönderir ve yanıtları konsol penceresine yazar. Yanıtların farklı biçimleri dikkat edin: XML, JSON, Atom ve XHTML.  
  
4.  .Jpeg biçiminde yanıt isteği bir URI gözatmak için istenir. Bir tarayıcı açın ve verilen URI göz atın.  
  
5.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Ayrıca Bkz.
