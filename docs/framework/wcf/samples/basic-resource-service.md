---
title: Temel Kaynak Hizmeti
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 2d55aecfdf6579b1de4c0cc324e59e23c251b12d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520142"
---
# <a name="basic-resource-service"></a>Temel Kaynak Hizmeti
Bu örnek, alma destekleyen, müşteriler topluluğu sunan Windows Communication Foundation (WCF) REST programlama modeli kullanarak bir HTTP tabanlı hizmet ekleme, ekleme, silme ve Değiştir işlemleri gösterilmektedir. Bu örnek 2 bileşenleri - şirket içinde barındırılan bir WCF HTTP hizmet (adını da) ve hizmet oluşturur ve bu çağrıları yapan bir konsol uygulaması (program.cs) oluşur.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 WCF hizmeti, müşteriler topluluğu kaynak odaklı/BEKLEYEN bir biçimde sunar. Kısacası, bu koleksiyonda koleksiyon müşteriler ve her müşteri için benzersiz bir URI'leri sahip içerir. Hizmet destekleyen bir HTTP gönderme `GET` tüm koleksiyon ve HTTP almak için URI koleksiyonu en `POST` koleksiyona yeni bir müşteri eklemek için URI toplama sırasında. Ayrıca HTTP desteklediği tek bir müşterinin URI'da `GET` Müşteri ayrıntıları, HTTP almak için `PUT` HTTP ve müşterinin ayrıntılarını değiştirmek için `DELETE` müşteri Koleksiyondan kaldırılacak. Koleksiyona yeni bir müşteri eklendiğinde, hizmet benzersiz bir URI atar ve URI müşterinin ayrıntılarını bir parçası olarak depolar. Ayrıca, yanıtın konumu HTTP üst bilgisi kullanarak istemciye URI iletir.  
  
 App.config dosyasını WCF Hizmeti ile bir varsayılan yapılandırır <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliğini `true`. Sonuç olarak, bir HTML tabanlı otomatik yardım sayfasına WCF oluşturur `http://localhost:8000/Customers/help` sağlayan HTTP oluşturmak hakkında bilgi müşteri ayrıntılarıdır nasıl bir örnek hizmeti ve hizmetin HTTP yanıtı – örneği için erişim istekleri XML ve JSON temsil edilir.  
  
 Müşteri koleksiyonunun gösterme (ve daha genel olarak, herhangi bir kaynak) bu şekilde istemcinin URI ve HTTP kullanmanın tek bir yolla etkileşime olanak tanır `GET`, `PUT`, `DELETE` ve `POST`. Program.cs gösterir böyle bir istemci nasıl olabileceğini kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bir WCF REST hizmeti erişmek için yalnızca bir yol olduğunu unutmayın. Diğer .NET Framework sınıflarını gibi hizmete erişmek mümkündür <xref:System.ServiceModel.ChannelFactory> ve <xref:System.Net.WebClient>. SDK diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) bir WCF Hizmeti ile iletişim kurmak için bu sınıflar kullanma işlemi gösterilmektedir.  
  
 Örnek şirket içinde barındırılan bir hizmet ve istemci oluşur. her ikisi de bir konsol uygulaması içinde çalıştırın. Konsol uygulamasının çalışır gibi istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Çözüm için temel kaynak hizmeti örneği açın. Başlatma sırasında [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde yürütmek için örnek için yönetici çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesini seçip **yönetici olarak çalıştır** bağlam menüsünden.  
  
2.  Çözümü derleyin ve konsol uygulamasını çalıştırmak için Ctrl + F5 tuşuna basın CTRL + SHIFT + B tuşlarına basın. Konsol penceresinde görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti. Herhangi bir noktada HTML Yardım sayfası URI Yardım sayfasının bir tarayıcıda yazarak görüntüleyebilirsiniz. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
3.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel HTTP Hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
