---
title: Windows Forms İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: c91f413cd5ef41fcbe85c083f2bcfb77a3c957a5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039875"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms İstemcisinde Veri Bağlama
Bu örnek, bir Windows Forms uygulamasında bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri Bu makalenin sonunda bulunur.  
  
 Bu örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan bir hizmeti gösterir. Örnek, bir istemci Windows Forms uygulamasından (. exe) ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Sözleşme, adlı `GetWeatherData`bir işlemi kullanıma `IWeatherService` sunan arabirim tarafından tanımlanır. Bu işlem bir şehir dizisini kabul eder ve bir şehirde yüksek ve `WeatherData` düşük tahmini sıcaklığın temsil ettiği nesne dizisini döndürür.  
  
 Veri bağlama Windows Forms uygulamasında istemcisinde oluşur. `DataGridView` , Verilerin grafik bir gösterimi olan Windows Forms tasarımcısında tanımlanır. Adlı `BindingSource` bir aracı da oluşturulur. Veri kaynağı `BindingSource` , hizmet tarafından döndürülen veri dizisine ayarlanır. Amacı `BindingSource` , veri ve veri görünümü arasında bir yöneltme katmanı sağlamaktır. Verilerle gezinme, sıralama, filtreleme ve güncelleştirme gibi tüm etkileşim, `BindingSource` bileşen çağrıları ile gerçekleştirilir. ' A veri `BindingSource` bağlamayı gerçekleştirmekiçin`DataGridView` , öğesinin'ınesnesineayarlanır.`datasource` `DataGridView` WCF hizmetinden döndürülen tüm veriler, Kullanıcı tarafından grafik olarak görüntülenir.  Kullanıcı düğmeye her tıkladığında döndürülen veriler otomatik olarak veri bağlantılı `DataGridView`olarak güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
