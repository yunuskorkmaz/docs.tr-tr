---
title: Temel Kaynak Hizmeti
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 62b2b863f38647e81468065fd69fc4933afc5b16
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803734"
---
# <a name="basic-resource-service"></a>Temel Kaynak Hizmeti
Bu örnek alma destekleyen müşteriler koleksiyonunu sunar Windows Communication Foundation (WCF) REST programlama modeli kullanarak bir HTTP tabanlı hizmet uygulamak, ekleme, silme ve değiştirme işlemlerini gösterir. Bu örnek 2 bileşenleri - kendini barındıran WCF HTTP hizmet (adını da) ve hizmet oluşturur ve bunu çağrılar bir konsol uygulaması (program.cs) oluşur.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 WCF hizmeti bir kaynak-yönelimli/REST şekilde müşteriler koleksiyonu kullanıma sunar. Kısacası, bu koleksiyonda koleksiyon müşteriler ve her müşteri için benzersiz URI'ler sahip içerir. Hizmet destekleyen bir HTTP gönderme `GET` koleksiyonunun tüm koleksiyon ve HTTP almak için URI `POST` koleksiyonunun yeni bir müşteri koleksiyona eklemek için URI. Ayrıca tek bir müşteri URI'de HTTP destekliyorsa `GET` Müşteri ayrıntıları, HTTP için `PUT` müşteri ve HTTP ayrıntılarını değiştirmek için `DELETE` müşteri Koleksiyondan kaldırılacak. Yeni bir müşteri koleksiyona eklendiğinde, hizmet benzersiz bir URI atar ve URI Müşteri'nin ayrıntılar bir parçası olarak depolar. Ayrıca, bu URI yanıt konum HTTP üstbilgisinin kullanan istemci iletişim kurar.  
  
 App.config dosyasını WCF Hizmeti ile bir varsayılan yapılandırır <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliğini `true`. Sonuç olarak, bir HTML tabanlı otomatik yardım sayfasına WCF oluşturur `http://localhost:8000/Customers/help` sağlayan HTTP oluşturmak hakkında bilgi, Müşteri ayrıntıları nasıl yapıldığını örneği hizmeti ve hizmetin HTTP yanıtı – örneği için erişim istekleri XML ve JSON temsil.  
  
 Müşteri koleksiyonu gösterme (ve daha genel olarak, herhangi bir kaynağa) bu şekilde istemcinin URI'ler ve HTTP kullanmanın tek bir yolla ile etkileşim olanak tanır `GET`, `PUT`, `DELETE` ve `POST`. Program.cs gösteren böyle bir istemci nasıl olabilir kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bu WCF REST hizmeti erişmenin tek yolu olduğuna dikkat edin. Diğer .NET Framework sınıfları gibi kullanarak hizmete erişmek mümkündür <xref:System.ServiceModel.ChannelFactory> ve <xref:System.Net.WebClient>. SDK'sındaki diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) bu sınıfların bir WCF Hizmeti ile iletişim için nasıl kullanılacağını gösterir.  
  
 Kendini barındıran hizmet ve bir istemci örnek oluşan her ikisi içinde bir konsol uygulamasını çalıştırın. Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Çözümü için temel kaynak hizmeti örneği açın. Başlatılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde çalıştırmak için örnek yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesini ve seçerek **yönetici olarak çalıştır** ve bağlam menüsünden.  
  
2.  Çözümü derlemek ve konsol uygulamasını çalıştırmak için Ctrl + F5 tuşuna basın CTRL + SHIFT + B tuşuna basın. Konsol penceresinde görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur. Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
3.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel HTTP Hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
