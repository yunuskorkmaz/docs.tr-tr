---
title: Kapsam ile Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 23991002a5236c491a9f74c7efe71ceb2bf51a37
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712073"
---
# <a name="discovery-with-scopes-sample"></a>Kapsam ile Keşif Örneği

Bu örnek, kullanılabilir uç noktaları kategorilere ayırmak için kapsamların nasıl kullanılacağını ve uç noktalar için zaman uyumsuz bir arama gerçekleştirmek üzere <xref:System.ServiceModel.Discovery.DiscoveryClient> nasıl kullanılacağını gösterir. Hizmette, bu örnek bir uç nokta bulma davranışı ekleyerek ve uç noktaya bir kapsam eklemek ve uç noktanın bulunabilirliğini denetlemek için kullanarak her bir uç nokta için bulmayı özelleştirmeyi gösterir. İstemcide, örnek, istemcilerin bir <xref:System.ServiceModel.Discovery.DiscoveryClient> nasıl oluşturacağından ve <xref:System.ServiceModel.Discovery.FindCriteria>kapsamlar ekleyerek kapsamları dahil etmek için arama parametrelerinin nasıl ince bir şekilde ayarlanacağına yönelik olarak geçer. Bu örnek ayrıca, bir sonlandırma ölçütü ekleyerek istemcilerin yanıtları nasıl kısıtlayabileceğini gösterir.

## <a name="service-features"></a>Hizmet özellikleri

Bu proje, <xref:System.ServiceModel.ServiceHost>eklenen iki hizmet uç noktasını gösterir. Her uç noktanın kendisiyle ilişkili bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> vardır. Bu davranış her iki uç nokta için URI kapsamları eklemek için kullanılır. Bu uç noktaların her birini ayırt etmek için kapsamlar kullanılır, böylelikle istemciler aramayı ince ayarlayabilirler. İkinci uç nokta için, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> özelliği `false`olarak ayarlanarak bulunabilirliği devre dışı bırakılabilir. Bu, bu uç noktayla ilişkili bulgu meta verilerinin herhangi bir bulma iletilerinin parçası olarak gönderilmemesini sağlar.

## <a name="client-features"></a>İstemci özellikleri

`FindCalculatorServiceAddress()` yöntemi, bir <xref:System.ServiceModel.Discovery.DiscoveryClient> kullanmayı ve iki kısıtlamayla bir <xref:System.ServiceModel.Discovery.FindCriteria> nasıl geçirileceğini gösterir. Ölçütlere bir kapsam eklenir ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özelliği 1 olarak ayarlanır. Kapsam sonuçları yalnızca aynı kapsamı yayınlayan hizmetlerle sınırlandırır. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 1 olarak ayarlamak, <xref:System.ServiceModel.Discovery.DiscoveryClient>, en fazla 1 uç nokta için beklediği yanıtları sınırlar. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> çağrısı, bir zaman aşımına ulaşılana veya bir uç nokta bulunana kadar iş parçacığını engelleyen zaman uyumlu bir işlemdir.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Ayrıntılar için bkz. [http ve https yapılandırma](https://go.microsoft.com/fwlink/?LinkId=70353) . Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komut şu şekilde çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Çözümü oluşturun.

3. Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.

4. İstemci yürütülebilir dosyasını çalıştırın. İstemcinin hizmeti bulabileceğini unutmayın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
