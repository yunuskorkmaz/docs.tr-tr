---
title: Form Gönderme
ms.date: 03/30/2017
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
ms.openlocfilehash: 005aba6ab8a8fcbe4f4e4f79055e04cff059f47d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503769"
---
# <a name="form-post"></a>Form Gönderme
Bu örnek, yeni gelen istek biçimlerinin desteklemek için WCF programlama modeli REST genişletmek gösterilmiştir. Örnek ayrıca, bir HTML form postasına isteğinden seri durumdan bir biçimlendirici uygulaması içeren bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü. Ayrıca, örnek bir T4 şablon kullanıcılar geri WCF REST hizmeti nakledebilirsiniz HTML formu sağlayan bir HTML sayfasına dönmek için kullanır.  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Gelen istek biçimlerinin genişletme desteği.  
  
-   T4 şablonları tümleştirme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek iki projeden oluşan. Bir projedir HTML form postalarınıza seri durumdan özel istek biçimlendirici içeren HtmlFormProcessing Kitaplığı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri. İkinci proje HtmlFormProcessing kitaplığının özel istek biçimlendirici kullanmak için temel kaynak hizmeti örnek genişleten bir konsol uygulamasıdır.  
  
 HTML formu gönderileri (HtmlFormRequestDispatchFormatter) seri durumdan özel biçimlendirici her ikisini de kabul [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanarak bir dize dönüştürülebilir türleri <xref:System.ServiceModel.Dispatcher.QueryStringConverter> ve türleri ile işaretlenen <xref:System.Runtime.Serialization.DataContractAttribute> olabilir üyeleri yalnızca sahip QueryStringConverter kullanarak bir dizeden dönüştürülür.  
  
 HtmlFormProcessing kitaplığı projesi da bir Özet temel sınıf içerir `RequestBodyDispatchFormatter`, diğer özel istek biçimlendiricileri oluşturmak için kullanılabilir. Türetme `RequestBodyDispatchFormatter` URI şablon parametreleri için işlemin yöntem parametreleri eşlemek temel sınıf sağlar istek gövdesi seri durumdan çıkarma mantığı odaklanmak Geliştirici sağlar. Ayrıca HtmlFormProcessing Kitaplığı'nda projedir `HtmlFormProcessingBehavior` öğesinden türetilen yapmayı gösteren sınıf <xref:System.ServiceModel.Description.WebHttpBehavior> varsayılan istek biçimlendirici özel istek biçimlendirici ile değiştirmek için.  
  
 Bu konsol uygulama projesi genişletir [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek. Temel kaynak hizmeti örneği, WCF REST programlama modeli kullanan bir şekilde bir kaynak kullanıma gösterilmiştir. Koleksiyondaki müşteriler oluşturulabilir, alınan, güncelleştirilmiş silinmiş ve şekilde temel kaynak hizmeti örnek bir müşteri koleksiyon kaynağı açıktır. Temel kaynak hizmeti örneği, yalnızca iki yerel olarak desteklenen gelen istek biçimi, XML ve JSON kullanır.  
  
 Bu Form Post örnek konsol uygulamasındaki kullanıcıların bir tarayıcı kullanarak bir HTML form post bir istek göndererek müşterilerin oluşturmasını sağlayan HtmlFormProcessing Kitaplığı'nda özel biçimlendirici kullanır. Ayrıca, hizmete geri postalama için formu içeren bir HTML sayfası döndüren bir işlem ekler. Bu HTML sayfası .tt dosyası ve bir otomatik olarak oluşturulan .cs dosyası oluşan bir önceden işlenmiş T4 şablon kullanılarak oluşturulur. .Tt dosya değişkenlerini içeren bir şablon biçiminde bir yanıt yazma ve yapıları denetlemek bir geliştirici sağlar. T4 hakkında daha fazla bilgi için bkz: [oluşturma yapıları tarafından kullanarak metin şablonlarını](http://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözümü için Form Post örneği açın. Başlatılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], örnek başarılı bir şekilde çalıştırmak için yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesi ve bağlam menüsünden "Yönetici olarak çalıştır" seçme.  
  
2.  Çözümü derlemek ve konsol uygulaması FormPost projesini çalıştırmak için CTRL + F5 tuşuna basın CTRL + SHIFT + B tuşuna basın.  
  
3.  Konsol penceresinde görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur.  
  
4.  Örnek çalışırken istemci geçerli etkinlik durumunu Yazar kullanılıp bunu ekleyerek bir müşteri, bir müşteri güncelleştirme, bir müşteri silme veya geçerli müşterilerin listesini konsol penceresine hizmetten alınıyor.  
  
5.  Müşteri formu URI'sini göz atmak için istenir. Bir tarayıcı açın ve verilen URI göz atın. Tür bir ad ve adres tıklatın ve müşteri için **gönderme** düğmesi.  
  
6.  Örnek çalıştırmaya devam etmek konsol penceresi için herhangi bir tuşa basın.  
  
7.  Örnek tamamladıkça tarayıcı kullanılarak oluşturulan müşteri müşteriler son listesinde bulunduğunu dikkat edin.  
  
8.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
