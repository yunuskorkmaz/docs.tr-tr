---
title: Kapsam ile Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 0d874116b90f423fbb78803a3641ef55fc848952
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508775"
---
# <a name="discovery-with-scopes-sample"></a>Kapsam ile Keşif Örneği
Bu örnek bulunabilirlik uç noktaları da nasıl kullanılacağını olarak sınıflandırmak için kapsamları kullanmayı gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient> uç noktaları için zaman uyumsuz bir arama gerçekleştirmek için. Hizmette her uç nokta için bulma uç noktası bulma davranışını ekleme ve uç noktasına bir kapsamı ekleme işlemi kullanılarak yanı sıra tarafından bitiş noktası bulunabilirliğini denetleme özelleştirme Bu örnek gösterir. İstemcide, örnek istemcileri nasıl oluşturacağınızı üzerinden giden bir <xref:System.ServiceModel.Discovery.DiscoveryClient> ve ince parametreleri kapsamına ekleyerek kapsamları eklemek için arama <xref:System.ServiceModel.Discovery.FindCriteria>. Ayrıca bu örnek bir sonlandırma ölçütüne ekleyerek istemciler yanıtları nasıl kısıtlayabilirsiniz gösterir.  
  
## <a name="service-features"></a>Hizmet Özellikleri  
 Bu proje, eklenen iki hizmet uç noktalarını gösterir. bir <xref:System.ServiceModel.ServiceHost>. Her bir uç noktası olan bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ilişkili. Bu davranış, iki uç noktalar için URI kapsamları eklemek için kullanılır. Kapsamları, böylece istemciler arama ince Bu uç noktaların her ayırt etmek için kullanılır. İkinci uç nokta için bulunabilirliği ayarlayarak devre dışı bırakılabilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> özelliğini `false`. Bu, bu uç nokta ile ilişkilendirilmiş bulma meta veri bulma iletileriniz bir parçası olarak gönderilmez sağlar.  
  
## <a name="client-features"></a>İstemci özellikleri  
 `FindCalculatorServiceAddress()` Yöntemi nasıl kullanılacağını gösteren bir <xref:System.ServiceModel.Discovery.DiscoveryClient> ve geçirin bir <xref:System.ServiceModel.Discovery.FindCriteria> iki kısıtlama. Bir kapsam ölçüte eklenir ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özelliği 1 olarak ayarlanır. Kapsam Sonuçları yalnızca aynı kapsamda yayımlama hizmetlerine sınırlar. Ayarı <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> yanıtları 1 sınırlar <xref:System.ServiceModel.Discovery.DiscoveryClient> en fazla 1 uç noktası için bekler. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Çağrıdır, bir zaman aşımı ulaşıldığında veya bir uç nokta bulundu kadar iş parçacığını engeller eşzamanlı bir işlem.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örneği çalıştırmak için doğru URL ACL eklenmesi gerekir. Bkz: [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için. Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir. Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Çözümü oluşturun.  
  
3.  Yürütülebilir hizmet oluşturma dizinden çalıştırın.  
  
4.  İstemci yürütülebilir çalıştırın. İstemci hizmetini bulun mümkün olduğunu unutmayın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a>Ayrıca bkz.
