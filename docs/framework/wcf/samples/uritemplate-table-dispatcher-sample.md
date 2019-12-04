---
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: e2ec85027274f302c59673a3d937be8f03d0b43b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715360"
---
# <a name="uritemplate-table-dispatcher-sample"></a>UriTemplate Tablosu Dağıtıcı Örneği
<xref:System.UriTemplateTable> sınıfı, bir <xref:System.UriTemplate> örnekleri kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar. Bu örnek, `UriTemplateTable` sınıfı için ortak bir kullanım senaryosu olan `UriTemplateTable`kullanılarak oluşturulan temel bir gönderme altyapısını gösterir.  
  
 Bu örnek `UriTemplateTable` sınıfı için aşağıdaki temel kavramları gösterir:  
  
- Temsilcileri bir `UriTemplateTable``UriTemplates` ile ilişkilendirme.  
  
- Belirli bir URI için doğru işleyici temsilcisini almak üzere <xref:System.UriTemplateTable.MatchSingle%2A> kullanma.  
  
- İsteği işlemek için işleyici temsilcisi çağrılıyor.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UriTemplate Tablosu](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
