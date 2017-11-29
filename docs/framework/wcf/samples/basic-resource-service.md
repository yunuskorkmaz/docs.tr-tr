---
title: Temel Kaynak Hizmeti
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8ba436cba284201f14635162ed394abfa9a14db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-resource-service"></a>Temel Kaynak Hizmeti
Bu örnek, bir HTTP tabanlı hizmet kullanarak uygulamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] alma destekleyen müşteriler koleksiyonu sunan REST programlama modeli ekleme, silme ve değiştirme işlemlerini. Bu örnek 2 bileşenleri - kendini barındıran oluşur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP hizmet (adını da) ve hizmet oluşturur ve bunu çağrılar bir konsol uygulaması (program.cs).  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmeti bir kaynak-yönelimli/REST şekilde müşteriler koleksiyonu kullanıma sunar. Kısacası, bu koleksiyonda koleksiyon müşteriler ve her müşteri için benzersiz URI'ler sahip içerir. Hizmet destekleyen bir HTTP gönderme `GET` koleksiyonunun tüm koleksiyon ve HTTP almak için URI `POST` koleksiyonunun yeni bir müşteri koleksiyona eklemek için URI. Ayrıca tek bir müşteri URI'de HTTP destekliyorsa `GET` Müşteri ayrıntıları, HTTP için `PUT` müşteri ve HTTP ayrıntılarını değiştirmek için `DELETE` müşteri Koleksiyondan kaldırılacak. Yeni bir müşteri koleksiyona eklendiğinde, hizmet benzersiz bir URI atar ve URI Müşteri'nin ayrıntılar bir parçası olarak depolar. Ayrıca, bu URI yanıt konum HTTP üstbilgisinin kullanan istemci iletişim kurar.  
  
 App.config dosyasını yapılandırır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan hizmet <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliğini `true`. Sonuç olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir HTML tabanlı otomatik yardım sayfasına oluşturur `http://localhost:8000/Customers/help` sağlayan HTTP oluşturmak hakkında bilgi, nasıl bir örneği hizmeti ve hizmetin HTTP yanıtı – örneği için erişim istekleri müşteri XML ve JSON Ayrıntılar gösterilir.  
  
 Müşteri koleksiyonu gösterme (ve daha genel olarak, herhangi bir kaynağa) bu şekilde istemcinin URI'ler ve HTTP kullanmanın tek bir yolla ile etkileşim olanak tanır `GET`, `PUT`, `DELETE` ve `POST`. Program.cs gösteren böyle bir istemci nasıl olabilir kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bu yalnızca bir erişmek için yolu olduğuna dikkat edin bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST hizmeti. Diğer .NET Framework sınıfları gibi kullanarak hizmete erişmek mümkündür <xref:System.ServiceModel.ChannelFactory> ve <xref:System.Net.WebClient>. SDK'sındaki diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) ile iletişim kurmak için bu sınıfları kullanmayı gösteren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
