---
title: "UriTemplate Tablosu Dağıtıcı Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d2332e5f23c46454d1a876c3e21c5a575d10bf5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="uritemplate-table-dispatcher-sample"></a>UriTemplate Tablosu Dağıtıcı Örneği
<xref:System.UriTemplateTable> Sınıfı, bir dizi birlikte çalışmaya yönelik bir sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar <xref:System.UriTemplate> örnekleri. Bu örnek kullanılarak oluşturulmuş bir temel dağıtırken altyapısı gösteren `UriTemplateTable`, genel bir kullanım senaryosu `UriTemplateTable` sınıfı.  
  
 Bu örnek için aşağıdaki anahtar kavramları göstermektedir `UriTemplateTable` sınıfı:  
  
-   Temsilcileri ile ilişkilendirme `UriTemplates` içinde bir `UriTemplateTable`.  
  
-   Kullanarak <xref:System.UriTemplateTable.MatchSingle%2A> belirli bir URI doğru işleyici temsilcisi elde edilir.  
  
-   İsteği işlemek için işleyici temsilcisi çağırma.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UriTemplate tablosu](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
