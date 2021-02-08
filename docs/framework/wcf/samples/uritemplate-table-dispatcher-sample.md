---
description: 'Daha fazla bilgi edinin: UriTemplate Tablo dağıtıcısı örneği'
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 68cd7e87c9768995210f369e2d55a10ad048e338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798205"
---
# <a name="uritemplate-table-dispatcher-sample"></a>UriTemplate Tablosu Dağıtıcı Örneği

<xref:System.UriTemplateTable>Sınıfı, bir örnek kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar <xref:System.UriTemplate> . Bu örnek `UriTemplateTable` , sınıfı için ortak bir kullanım senaryosu kullanılarak oluşturulan temel bir gönderme altyapısını gösterir `UriTemplateTable` .  
  
 Bu örnek, sınıfı için aşağıdaki temel kavramları gösterir `UriTemplateTable` :  
  
- Temsilcileri bir ile ilişkilendirme `UriTemplates` `UriTemplateTable` .  
  
- <xref:System.UriTemplateTable.MatchSingle%2A>Belirli BIR URI için doğru işleyici temsilcisini almak için kullanma.  
  
- İsteği işlemek için işleyici temsilcisi çağrılıyor.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UriTemplate Tablosu](uritemplate-table-sample.md)
- [UriTemplate](uritemplate-sample.md)
