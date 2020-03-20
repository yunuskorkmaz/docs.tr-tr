---
title: Windows Forms İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d538e8a525f8d07e9ac9f57d4b10119907602d90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145052"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms İstemcisinde Veri Bağlama
Bu örnek, windows forms uygulamasında bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilere nasıl bağlanılabildiğini gösterir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu makalenin sonunda yer alır.  
  
 Bu örnek, istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmet gösterir. Örnek, bir istemci Windows Forms uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Sözleşme, adı verilen `IWeatherService` `GetWeatherData`bir işlemi ortaya çıkaran arabirim tarafından tanımlanır. Bu işlem bir dizi şehri kabul eder `WeatherData` ve bir şehir için yüksek ve düşük tahmin edilen sıcaklığı temsil eden bir dizi nesne döndürür.  
  
 Veri bağlama, Windows Forms uygulamasında istemcide oluşur. A, `DataGridView` verilerin grafiksel bir temsili olan Windows Forms tasarımcısında tanımlanır. Adlı `BindingSource` bir aracı da oluşturulur. Veri kaynağı, `BindingSource` hizmet tarafından döndürülen veri dizisine ayarlanır. Amacın amacı, `BindingSource` veri ve veri görünümü arasında bir yönlendirme katmanı sağlamaktır. Gezinme, sıralama, filtreleme ve güncelleştirme gibi verilerle tüm etkileşim `BindingSource` bileşene yapılan çağrılarla gerçekleştirilir. Veri bağlama gerçekleştirmek `DataGridView`için `datasource` , `DataGridView` sonra `BindingSource` nesneye ayarlanır. WCF hizmetinden döndürülen tüm veriler daha sonra kullanıcıya grafik olarak görüntülenir.  Kullanıcı düğmeyi her tıklattığınızda, döndürülen veriler veriye bağlı `DataGridView`olarak otomatik olarak güncelleştirilir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
