---
title: UriTemplate Örneği
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 55999167d99069a4b207f4deda42f48bf02e1bdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294969"
---
# <a name="uritemplate-sample"></a>UriTemplate Örneği

<xref:System.UriTemplate>Sınıfı, ortak bir yapıyı paylaşan URI kümeleriyle çalışmak için yöntemler sağlar. Bu örnek, ile ilgili aşağıdaki temel kavramları göstermektedir `UriTemplate` :  
  
- Şablon oluşturma sözdizimi.  
  
- Bir `UriTemplate` using ve kullanarak URI 'leri örnekleme <xref:System.UriTemplate.BindByName%2A> <xref:System.UriTemplate.BindByPosition%2A> .  
  
- <xref:System.UriTemplateTable.Match%2A>, ve ' nin ters işlemidir `BindByName` `BindByPosition` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UriTemplate Tablosu](uritemplate-table-sample.md)
- [UriTemplate Tablosu Dağıtıcısı](uritemplate-table-dispatcher-sample.md)
