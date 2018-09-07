---
title: Form Gönderme
ms.date: 03/30/2017
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
ms.openlocfilehash: 9115b9abfa7039bf409bb9bbce54e5012d05a074
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44077021"
---
# <a name="form-post"></a>Form Gönderme
Bu örnek nasıl yeni gelen istek biçimlerinin desteklemek için WCF programlama modeli REST genişletileceğini gösterir. Örnek bir HTML form gönderiyi gelen isteği seri durumdan bir biçimlendirici uygulaması da içerir. bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü. Ayrıca, örnek, kullanıcıların WCF REST hizmetine gönderebilir HTML form sağlayan bir HTML sayfasına dönmek için T4 şablonu kullanır.  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Gelen istek biçimlerinin desteğini genişletme.  
  
-   T4 şablonları tümleştirme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek iki projeden oluşan. Bir proje olan HTML form postalarınıza seri durumdan çıkarabiliyorsa bir özel talep biçimlendirici içeren HtmlFormProcessing Kitaplığı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri. İkinci proje özel istek biçimlendirici HtmlFormProcessing kitaplığı kullanmak için temel kaynak hizmeti örneği genişleten bir konsol uygulamasıdır.  
  
 HTML form gönderilerini (HtmlFormRequestDispatchFormatter) seri durumdan çıkarabiliyorsa özel biçimlendirici hem kabul ettiği [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanarak bir dize dönüştürülebilir türleri <xref:System.ServiceModel.Dispatcher.QueryStringConverter> ve ile işaretlenen türler <xref:System.Runtime.Serialization.DataContractAttribute> olabilir üyeleri yalnızca sahip QueryStringConverter kullanarak bir dizeden dönüştürülür.  
  
 HtmlFormProcessing kitaplığı projesi, ayrıca bir soyut temel sınıf içerir `RequestBodyDispatchFormatter`, diğer özel istek biçimlendiricileri oluşturmak için kullanılabilir. Öğesinden türetme `RequestBodyDispatchFormatter` bir geliştiricinin URI şablonu parametreleri işlemin yöntemi parametrelerine eşleştirmek temel sınıf sağlar istek gövdesi seri durumdan çıkarma mantıksal odaklanmasını sağlar. Ayrıca HtmlFormProcessing kitaplıkta projedir `HtmlFormProcessingBehavior` öğesinden türetilen yapmayı gösteren sınıf <xref:System.ServiceModel.Description.WebHttpBehavior> varsayılan isteği biçimlendirici bir özel talep biçimlendirici ile değiştirilecek.  
  
 Bu konsol uygulama projesi genişletir [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek. Temel kaynak hizmeti örneği, WCF REST programlama modeli kullanan bir şekilde bir kaynak kullanıma sunmak gösterilmektedir. Müşteriler koleksiyondaki oluşturulabilir, alınan, güncelleştirilmiş silindi ve şekilde temel kaynak hizmeti örnek bir müşteri koleksiyonu kaynağı kullanıma sunulur. Temel kaynak hizmeti örnek yalnızca iki yerel olarak desteklenen gelen isteği biçimleri, XML ve JSON kullanır.  
  
 Bu formu örnek konsol uygulaması, kullanıcıların bir tarayıcı kullanarak bir HTML form postası bir istek göndererek müşterilerin oluşturmasını sağlayan HtmlFormProcessing Kitaplığı'nda özel biçimlendirici kullanır. Ayrıca, hizmete geri gönderilecek formu içeren bir HTML sayfası döndüren bir işlem ekler. Bu HTML sayfası .tt dosyası ve bir otomatik olarak oluşturulan .cs dosyası oluşan bir Önişlenmiş T4 şablonu kullanılarak oluşturulur. .Tt dosyayı değişkenlerini içeren bir şablon biçimde yanıt yazın ve yapıları denetlemek bir geliştirici sağlar. T4 hakkında daha fazla bilgi için bkz: [oluşturma yapıları tarafından kullanarak metin şablonlarını](https://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözüm için Form Post örneği açın. Başlatma sırasında [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], örnek başarıyla yürütmek için yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesi ve bağlam menüsünden "Yönetici olarak çalıştır" seçme.  
  
2.  Çözümü derleyin ve konsol uygulaması FormPost projeyi çalıştırmak için CTRL + F5 tuşuna basın CTRL + SHIFT + B tuşlarına basın.  
  
3.  Konsol penceresinde görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti.  
  
4.  Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar mı bunu ekleyerek bir müşteri, bir müşteri güncelleştiriliyor, bir müşteri siliniyor veya geçerli müşterilerin listesini konsol penceresine hizmetten alınıyor.  
  
5.  Ardından, müşteri formu URI'sini göz atmak için istenir. Bir tarayıcı açın ve verilen URI için göz atın. Bir ad ve tıklayın ve müşteri adresi yazın **Gönder** düğmesi.  
  
6.  Konsol penceresinde, örnek çalıştırmaya devam etmek için herhangi bir tuşa basın.  
  
7.  Örnek tamamladıkça, tarayıcı kullanarak oluşturduğunuz müşteri müşteriler son listede bulunduğunu dikkat edin.  
  
8.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
