---
title: Hiyerarşik Yapılandırma Modeli
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 8ca9b01eb022e2e2ab940866a6230e8227ceb2dc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736399"
---
# <a name="hierarchical-configuration-model"></a>Hiyerarşik Yapılandırma Modeli
Bu örnek, uygulama hizmetleri için yapılandırma dosyalarını hiyerarşisini gösterir. Ayrıca, uç nokta davranışları bağlamaları ve hizmet davranışlarını hiyerarşideki üst düzey nasıl devralınır gösterir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 WCF'de için geliştirilen özelliklerinden [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] hiyerarşik yapılandırma modeli iyileştirmedir. Hiyerarşik yapılandırma modeli örnek verilebilir Machine.config tarafından tanımlanan bir Rootweb.config -> Web.config ->. İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], hizmetlerinizi açık bir yapılandırma gerekmeden bu bağlamaları ve yapılandırma hiyerarşideki üst düzey tanımlanan davranışları eklenir. Bu örnek nasıl bilgisayar veya uygulama düzeyinde tanımlanan yapılandırma öğeleri bağlı hizmet yapılandırmanızı basitleştirmek mümkün olduğunu gösterir.  
  
 Bu örnek dokuz Hizmetleri, üç hiyerarşi düzeylerinde tanımlı oluşur. `Service1` kök dizininde ' dir. `Service2` ve `Service3` varsayılan öğelerden devralınan `Service1`. `Service4`, `Service5`, `Service6` ve `Service7` varsayılan öğeleri devralma hiyerarşisinin üçüncü bir düzeyde tanımlanan `Service3`. Son olarak `Service10` ve `Service11` dördüncü hiyerarşisini düzeyi olan.  
  
 Tüm hizmetleri uygulayan `IDesc` sözleşme. Aşağıdaki tanımıdır `IDesc` bu arabirimde kullanıma sunulan yöntemleri gösteren arabirimi. `IDesc` Arabirimi Service1.cs içinde tanımlanır.  
  
```csharp  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 Uygulama Hizmetleri tarafından bu yöntemlerin oldukça basittir. `ListEndpoints` tüm hizmet uç noktaları yinelenir ve hizmetin tüm uç noktalar listesi döndürür. `ListServiceBehaviors` Bu hizmete eklenen tüm davranışları gezinir ve hizmetle ilişkili hizmet davranışları listesini döndürür. `ListEndpointBehaviors` benzer şekilde davranır `ListServiceBehaviors`, ancak bunun yerine uç nokta davranışları listesini döndürür.  
  
 Bu uygulama, hizmet kaç uç noktaları öğrenmek için istemci gösterme ve hangi hizmet davranışları ve uç nokta davranışları hizmetine eklenmiştir sağlar. Örnek bir parçası olarak uygulanan istemci, Çözümdeki tüm hizmetler için bir hizmet başvurusu ekler ve bu hizmetlerin her biri, öğeleri gösterir.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
#### <a name="to-run-the-client"></a>İstemciyi çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ConfigHierarchicalModel.sln dosyasını açın.  
  
2.  İstemci projeyi başlangıç projesi olarak ayarlamış değil, aşağıdaki adımları izleyin.  
  
    1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **özellikleri**.  
  
    2.  İçinde **ortak özellikler**seçin **başlangıç projesi**ve ardından **tek başlangıç projesi**.  
  
    3.  Gelen **tek başlangıç projesi** açılan listesinde, select **istemci**.  
  
    4.  Tıklayın **Tamam** iletişim kutusunu kapatmak için.  
  
3.  Örneği oluşturmak için CTRL + SHIFT + B tuşlarına basın.  
  
4.  İstemciyi çalıştırmak için Ctrl + F5 tuşlarına basın.  
  
> [!NOTE]
>  Bu adımlar da işe yaramazsa, ortamınızı düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığından emin olun:  
>   
> 1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](building-the-samples.md).  
> 3.  Tek bir veya birden çok bilgisayar yapılandırmalarını örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric Yönetimi örnekleri](https://go.microsoft.com/fwlink/?LinkId=193960)
