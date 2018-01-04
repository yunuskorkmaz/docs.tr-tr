---
title: "Kapsam ile Keşif Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa762df1dbfe92102f8cd719613099b23986ed0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-with-scopes-sample"></a>Kapsam ile Keşif Örneği
Bu örnek kapsamları bulunabilirlik uç noktaları iyi nasıl kullanılacağını olarak kategorilere ayırmak için nasıl kullanılacağını göstermektedir <xref:System.ServiceModel.Discovery.DiscoveryClient> uç noktalar için zaman uyumsuz bir arama yapmak üzere. Hizmette Bu örnek bulma her uç nokta için bir uç nokta bulma davranışını ekleme ve uç nokta için bir kapsam eklemek için kullanarak yanı sıra uç noktanın bulunabilirliği denetleme özelleştirme gösterilmektedir. İstemcilerin nasıl oluşturabileceğinizi üzerinden örnek istemcide, giden bir <xref:System.ServiceModel.Discovery.DiscoveryClient> ve kapsamları ekleyerek kapsamları eklenecek parametreleri arama ince ayar <xref:System.ServiceModel.Discovery.FindCriteria>. Bu örnek ayrıca bir sonlandırma ölçüt ekleyerek istemcileri yanıtları nasıl kısıtlayabilirsiniz gösterir.  
  
## <a name="service-features"></a>Hizmet Özellikleri  
 Bu proje için eklenmekte olan iki hizmet uç noktaları gösterir bir <xref:System.ServiceModel.ServiceHost>. Her bitiş noktasının bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> kendisiyle ilişkilendirilmiş. Bu davranış, her iki uç noktaları için URI kapsamı eklemek için kullanılır. Kapsamları, böylece istemciler arama yapılandırarak ince ayar her Bu uç noktalar ayırt etmek için kullanılır. İkinci uç nokta için bulunabilirliği ayarlayarak devre dışı bırakılabilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> özelliğine `false`. Bu, herhangi bir bulma iletisinin bir parçası olarak bu uç noktasıyla ilişkili bulma meta veri gönderilmez sağlar.  
  
## <a name="client-features"></a>İstemci özellikleri  
 `FindCalculatorServiceAddress()` Yönteminin nasıl kullanılacağını gösterir bir <xref:System.ServiceModel.Discovery.DiscoveryClient> ve geçirin bir <xref:System.ServiceModel.Discovery.FindCriteria> iki kısıtlamalarla. Bir kapsam ölçüte eklenir ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özelliğini 1 olarak ayarlayın. Kapsam yalnızca aynı kapsamı yayımlama hizmetlerine sonuçlarını sınırlandırır. Ayarı <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 1 yanıtları sınırlar <xref:System.ServiceModel.Discovery.DiscoveryClient> için en fazla 1 uç nokta bekler. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Çağrıdır zaman aşımı sınıra veya bir uç nokta bulundu kadar iş parçacığı engellenir eşzamanlı bir işlem.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örneği çalıştırmak için doğru URL ACL eklenmesi gerekir. Bkz: [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için. Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir. Komut olduğu gibi çalışmazsa, etki alanı ve kullanıcı adı şu bağımsız değişkenleri yerine isteyebilirsiniz:`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Çözümü oluşturun.  
  
3.  Hizmeti yürütülebilir dosyası derleme dizininden çalıştırın.  
  
4.  İstemci yürütülebilir çalıştırın. İstemci hizmetini bulun mümkün olduğunu unutmayın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>Ayrıca Bkz.
