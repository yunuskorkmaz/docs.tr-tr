---
title: Windows Forms İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: 6ad71555148ed4f907483b677097e1f673373d87
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336947"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms İstemcisinde Veri Bağlama
Bu örnek, bir Windows Forms uygulamasında bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen veri bağlamak nasıl gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri bu makalenin sonunda yer alır.  
  
 Bu örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmette gösterir. Örnek, bir istemcinin Windows Forms uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir WCF Hizmeti oluşur.  
  
 Anlaşma tarafından tanımlanan `IWeatherService` adlı bir işlem sunan arabirimi `GetWeatherData`. Bu işlem, bir dizi şehirlerin kabul eder ve bir dizi döndürür `WeatherData` bir şehir için tahmin edilen yüksek ve düşük sıcaklık temsil eden nesneleri.  
  
 Windows Forms uygulamasında istemcisinde veri bağlama gerçekleşir. A `DataGridView` veri grafik gösterimi olan Windows Form Tasarımcısı'nda tanımlanır. Adlı bir aracı `BindingSource` da oluşturulur. Veri kaynağını `BindingSource` hizmet tarafından döndürülen veri dizisi ayarlanır. Amacı `BindingSource` katmanındaki veriler ve veri görünümü arasında bir yöneltme sağlamaktır. Gezinme, sıralama, filtreleme ve güncelleştirme gibi veri tüm etkileşim çağrılarıyla gerçekleştirilir `BindingSource` bileşeni. Veri bağlama gerçekleştirmek için `DataGridView`, `datasource` , `DataGridView` sonra ayarlanır `BindingSource` nesne. Tüm WCF hizmetten döndürülen veriler görüntülenir grafik kullanıcıya.  Kullanıcının düğmesini her tıklayışında, döndürülen veriler verilere bağlı otomatik olarak güncelleştirilir `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
