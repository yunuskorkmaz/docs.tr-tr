---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36807ce154ab70e54d211405e0cea5ead56e9b88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="overloadgroups"></a>OverloadGroups
Bu örnek bir etkinliğin oluşur (`CreateLocation`), iki ilginç özelliklere sahiptir:  
  
1.  Bu bazı bağımsız değişkenler ve bazı isteğe bağlı olanları istedi.  
  
2.  Kullanıcının bağımsız değişkenlerinin iki farklı kümesinden sağlamak seçmesine izin verir.  
  
 Bu davranışların bu iki özellik kullanılarak gerçekleştirilebilir:  
  
-   `[isRequired]`belirli bir etkinliğe Ata özelliğidir ve aksi durumda, bir özel durum oluşturur doğrular.  
  
-   `[OverloadGroup]`bir küme veya başka bir kullanma arasında kullanıcı etkinliğinin seçebilmeleri birlikte bağımsız değişkenleri, bir dizi koyar. Kullanıcı farklı gruplardan aşırı yükleme bağımsız değişkenleri aynı örneğinde kullanamaz.  
  
 Farklı iş akışlarını ayarladıktan sonra arama <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.Constraint>. Yazdırma <xref:System.Activities.Validation.Constraint> konsoluna nesneleri.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Açık **OverloadGroups.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
