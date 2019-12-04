---
title: Windows Forms İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: 70bb47ff13e639bd34ad4df2f5aa6f09fb00b41d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716381"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms İstemcisinde Veri Bağlama
Bu örnek, bir Windows Forms uygulamasında bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri Bu makalenin sonunda bulunur.  
  
 Bu örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan bir hizmeti gösterir. Örnek, bir istemci Windows Forms uygulamasından (. exe) ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Sözleşme, `GetWeatherData`adlı bir işlem sunan `IWeatherService` arabirimi tarafından tanımlanır. Bu işlem bir şehir dizisini kabul eder ve bir şehirde yüksek ve düşük tahmin edilen sıcaklığı temsil eden `WeatherData` nesnelerden oluşan bir dizi döndürür.  
  
 Veri bağlama Windows Forms uygulamasında istemcisinde oluşur. `DataGridView`, verilerin grafik bir gösterimi olan Windows Forms tasarımcısında tanımlanmıştır. `BindingSource` adlı bir aracı da oluşturulur. `BindingSource` veri kaynağı, hizmet tarafından döndürülen veri dizisine ayarlanır. `BindingSource` amacı, veri ve veri görünümü arasında bir yöneltme katmanı sağlamaktır. Verilerle gezinme, sıralama, filtreleme ve güncelleştirme gibi tüm etkileşimler `BindingSource` bileşeni çağrılarında gerçekleştirilir. `DataGridView`veri bağlamayı gerçekleştirmek için `DataGridView` `datasource` `BindingSource` nesnesine ayarlanır. WCF hizmetinden döndürülen tüm veriler, Kullanıcı tarafından grafik olarak görüntülenir.  Kullanıcı düğmeye her tıkladığında döndürülen veriler, veri bağlantılı `DataGridView`otomatik olarak güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
