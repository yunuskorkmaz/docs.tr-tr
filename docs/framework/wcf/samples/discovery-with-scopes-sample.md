---
title: Kapsam ile Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 9b65a348c943b07e813e3fe690f1364b77a94890
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972011"
---
# <a name="discovery-with-scopes-sample"></a>Kapsam ile Keşif Örneği

Bu örnek, keşfedilebilir uç noktaları <xref:System.ServiceModel.Discovery.DiscoveryClient> kategorilere ayırmak için kapsamların nasıl kullanılacağını ve uç noktalar için zaman uyumsuz bir arama yapmayı nasıl kullanacağınızı gösterir. Hizmette, bu örnek bir uç nokta bulma davranışı ekleyerek ve uç noktaya bir kapsam eklemek ve uç noktanın bulunabilirliğini denetlemek için kullanarak her bir uç nokta için bulmayı özelleştirmeyi gösterir. İstemcide, örnek, istemcilerinin ' a kapsam <xref:System.ServiceModel.Discovery.DiscoveryClient> <xref:System.ServiceModel.Discovery.FindCriteria>ekleyerek kapsamları dahil etmek için arama parametrelerini nasıl oluşturup ayarlayaacağına dair bir süre boyunca gider. Bu örnek ayrıca, bir sonlandırma ölçütü ekleyerek istemcilerin yanıtları nasıl kısıtlayabileceğini gösterir.

## <a name="service-features"></a>Hizmet özellikleri

Bu proje, bir <xref:System.ServiceModel.ServiceHost>öğesine eklenen iki hizmet uç noktasını gösterir. Her uç noktanın kendisiyle <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ilişkili bir ilişkisi vardır. Bu davranış her iki uç nokta için URI kapsamları eklemek için kullanılır. Bu uç noktaların her birini ayırt etmek için kapsamlar kullanılır, böylelikle istemciler aramayı ince ayarlayabilirler. İkinci uç nokta için, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> özelliği olarak `false`ayarlanarak bulunabilirliği devre dışı bırakılabilir. Bu, bu uç noktayla ilişkili bulgu meta verilerinin herhangi bir bulma iletilerinin parçası olarak gönderilmemesini sağlar.

## <a name="client-features"></a>İstemci özellikleri

Yöntemi `FindCalculatorServiceAddress()` , <xref:System.ServiceModel.Discovery.DiscoveryClient> ' nin nasıl kullanılacağını ve iki kısıtlama <xref:System.ServiceModel.Discovery.FindCriteria> ile nasıl geçirileceğini gösterir. Ölçütlere bir kapsam eklenir ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Özellik 1 olarak ayarlanır. Kapsam sonuçları yalnızca aynı kapsamı yayınlayan hizmetlerle sınırlandırır. 1 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> olarak ayarlandığında, en çok, <xref:System.ServiceModel.Discovery.DiscoveryClient> 1 uç nokta için beklediği yanıtları sınırlar. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Çağrı, zaman aşımına ulaşılıncaya veya bir uç nokta bulunana kadar iş parçacığını engelleyen zaman uyumlu bir işlemdir.

### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Ayrıntılar için bkz. [http ve https yapılandırma](https://go.microsoft.com/fwlink/?LinkId=70353) . Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komut şu şekilde çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz:`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Çözümü oluşturun.

3. Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.

4. İstemci yürütülebilir dosyasını çalıştırın. İstemcinin hizmeti bulabileceğini unutmayın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
