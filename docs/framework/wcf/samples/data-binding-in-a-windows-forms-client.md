---
title: "Windows Forms İstemcisinde Veri Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 905d010c1ecdab1fc7b2c99e6d720b85ad40be32
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows Forms İstemcisinde Veri Bağlama
Bu örnek tarafından döndürülen veri bağlamak nasıl gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir Windows Forms uygulamasında hizmet.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve yapı yönergeleri bu makalenin sonunda yer alır.  
  
 Bu örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir hizmeti gösterir. Örnek bir Windows Forms uygulaması (.exe) istemcisi oluşur ve bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Internet Information Services (IIS) tarafından barındırılan hizmeti.  
  
 Anlaşma tarafından tanımlanan `IWeatherService` adlı bir işlem kullanıma sunan arabirim `GetWeatherData`. Bu işlem bir dizi Şehir kabul eder ve bir dizi döndürür `WeatherData` bir şehir için yüksek ve düşük tahmin edilen sıcaklık temsil eden nesne.  
  
 Windows Forms uygulamasında istemcisinde veri bağlama oluşur. A `DataGridView` verileri grafik gösterimi olan Windows Forms Tasarımcısı'nda tanımlanır. Adlı bir aracı `BindingSource` da oluşturulur. Veri kaynağı `BindingSource` hizmet tarafından döndürülen veri dizisi ayarlanır. Amacı `BindingSource` yöneltme verileri ve veri görünümü arasında bir katmanı sağlamaktır. Gezinme, sıralama, filtreleme ve güncelleştirilmesi gibi verilere tüm etkileşim çağrıları ile gerçekleştirilir `BindingSource` bileşeni. Veri bağlama gerçekleştirmek için `DataGridView`, `datasource` , `DataGridView` sonra ayarlanır `BindingSource` nesnesi. Döndürülen verilerin tümünü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sonra görüntülenen grafik kullanıcıya.  Kullanıcı düğmesine tıklar her zaman, döndürülen veriler içinde veri bağlama otomatik olarak güncelleştirilir `DataGridView`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a>Ayrıca Bkz.
