---
title: Windows Forms İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d2784c86bc3ef84f99f4731f441019b3f568b321
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575491"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms İstemcisinde Veri Bağlama
Bu örnek, bir Windows Forms uygulamasında bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verilerin nasıl bağlanacağını gösterir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri Bu makalenin sonunda bulunur.  
  
 Bu örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan bir hizmeti gösterir. Örnek, bir istemci Windows Forms uygulamasından (. exe) ve Internet Information Services (IIS) tarafından barındırılan bir WCF hizmetinden oluşur.  
  
 Sözleşme, `IWeatherService` adlı bir işlemi kullanıma sunan arabirim tarafından tanımlanır `GetWeatherData` . Bu işlem bir şehir dizisini kabul eder ve `WeatherData` bir şehirde yüksek ve düşük tahmini sıcaklığın temsil ettiği nesne dizisini döndürür.  
  
 Veri bağlama Windows Forms uygulamasında istemcisinde oluşur. `DataGridView`, Verilerin grafik bir gösterimi olan Windows Forms tasarımcısında tanımlanır. Adlı bir aracı `BindingSource` da oluşturulur. Veri kaynağı, `BindingSource` hizmet tarafından döndürülen veri dizisine ayarlanır. Amacı, `BindingSource` veri ve veri görünümü arasında bir yöneltme katmanı sağlamaktır. Verilerle gezinme, sıralama, filtreleme ve güncelleştirme gibi tüm etkileşim, bileşen çağrıları ile gerçekleştirilir `BindingSource` . ' A veri bağlamayı gerçekleştirmek için, `DataGridView` `datasource` öğesinin ' `DataGridView` ı nesnesine ayarlanır `BindingSource` . WCF hizmetinden döndürülen tüm veriler, Kullanıcı tarafından grafik olarak görüntülenir.  Kullanıcı düğmeye her tıkladığında döndürülen veriler otomatik olarak veri bağlantılı olarak güncelleştirilir `DataGridView` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
