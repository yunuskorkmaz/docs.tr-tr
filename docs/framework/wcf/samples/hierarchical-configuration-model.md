---
title: Hiyerarşik Yapılandırma Modeli
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 4debeaf0bfd2558552a7943f3767a4f9b53ce550
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hierarchical-configuration-model"></a>Hiyerarşik Yapılandırma Modeli
Bu örnek, hizmetler için yapılandırma dosyalarını hiyerarşisini uygulamak gösterilmiştir. Aynı zamanda, nasıl bağlamaları, hizmet davranışları ve uç nokta davranışları hiyerarşide daha yüksek bir düzeyinden devralınan gösterir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Özellikler geliştirilen için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içinde [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] hiyerarşik yapılandırma modeli iyileştirme. Hiyerarşik yapılandırma modeli örneği olacaktır Machine.config tarafından tanımlanan bir Rootweb.config -> Web.config ->. İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], bu bağlamalar ve yapılandırma hiyerarşideki üst düzey tanımlanan davranışları hizmetlerinize hiçbir açık yapılandırmasıyla eklenir. Bu örnek nasıl bilgisayar veya uygulama düzeyinde tanımlanan yapılandırma öğeleri güvenmek, hizmet yapılandırmasını basitleştirmek olası olduğunu gösterir.  
  
 Bu örnek dokuz Hizmetleri, üç düzeyde hiyerarşi içinde tanımlı oluşur. `Service1` kök dizininde ' dir. `Service2` ve `Service3` varsayılan öğelerinden devralır `Service1`. `Service4`, `Service5`, `Service6` ve `Service7` varsayılan öğeleri devralma hiyerarşisi, üçüncü bir düzeyde tanımlanan `Service3`. Son olarak `Service10` ve `Service11` dördüncü hiyerarşisini düzeyi şunlardır.  
  
 Tüm hizmetler uygulamak `IDesc` sözleşme. Aşağıdaki tanımıdır `IDesc` arabirimi bu arabirimde kullanıma sunulan yöntemleri gösterir. `IDesc` Arabirimi service1.cs dosyasını tanımlanır.  
  
```  
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
  
 Uygulama Hizmetleri tarafından bu yöntemlerin basittir. `ListEndpoints` tüm hizmet uç noktaları yoluyla ilerler ve hizmetin tüm uç noktaları listesini döndürür. `ListServiceBehaviors` hizmetine eklediğiniz tüm davranışları dolaşır ve hizmetle ilişkilendirilmiş tüm hizmet davranışları listesini döndürür. `ListEndpointBehaviors` benzer şekilde davranır `ListServiceBehaviors`, ancak bunun yerine uç nokta davranışları listesini döndürür.  
  
 Bu uygulama, hizmet kaç tane uç noktaları bilmeniz istemci gösterme ve hangi hizmet davranışları ve uç nokta davranışları hizmete eklenmiştir sağlar. Örnek bir parçası olarak uygulanan istemci Çözümdeki tüm Hizmetleri hizmeti başvuru ekler ve hizmetlerinin her biri için bu öğeler gösterilir.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
#### <a name="to-run-the-client"></a>İstemci çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ConfigHierarchicalModel.sln dosyasını açın.  
  
2.  İstemci projesi zaten başlangıç projesi olarak kurulu değil, şu adımları izleyin.  
  
    1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve ardından **özellikleri**.  
  
    2.  İçinde **ortak özellikleri**seçin **başlangıç projesi**ve ardından **tek başlangıç projesi**.  
  
    3.  Gelen **tek başlangıç projesi** açılan listesinde, select **istemci**.  
  
    4.  Tıklatın **Tamam** iletişim kutusunu kapatmak için.  
  
3.  Örneği oluşturmak için CTRL + SHIFT + B tuşuna basın.  
  
4.  İstemci çalıştırmak için Ctrl + F5 tuşuna basın.  
  
> [!NOTE]
>  Bu adımlar işe yaramazsa, ortamınızın düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığını emin olun.  
>   
>  1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Tek bir veya birden çok bilgisayar yapılandırması örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric Yönetimi örnekleri](http://go.microsoft.com/fwlink/?LinkId=193960)
