---
title: "Etkinlik ilişkileri doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93cb5e93791c001e3795408a4c6b77be772f26e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-relationships-validation"></a>Etkinlik ilişkileri doğrulama
Bu örnek üç etkinliklerinin oluşur `CreateCity`, `CreateState`, ve `CreateCountry`. `CreateCity`içinde olmalıdır bir `CreateState` etkinliği ve `CreateState` içinde olmalıdır bir `CreateCountry` etkinlik. Bu örnek amacıyla kod için doğrulama mantığını bulunduğu `CreateState` etkinliği ve XAML için `CreateCity` etkinlik. Her iki kısıtlamaları aynı davranışı sahiptir.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Etkinlikleri arasındaki ilişkileri doğrulamak Geliştirici izin aşağıdaki üç Yardımcısı etkinlikler sağlar:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Geçerli düğüm üst öğeye ait tüm etkinliklerin koleksiyonunu sağlar  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Geçerli düğüm hariç geçerli düğüm alt ağacına ait tüm etkinliklerin koleksiyonunu sağlar  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Geçerli düğüm aynı ağaç tüm etkinliklerin koleksiyonunu sağlar  
  
 Örnekte, bir <xref:System.Activities.Statements.ForEach%601> etkinlik tarafından döndürülen koleksiyonunun rehberlik için kullanılan <xref:System.Activities.Validation.GetParentChain>. Türünü karşılaştırılır koleksiyondaki her öğe için `CreateCountry` (veya `CreateState` varsa `CreateCity` Doğrulanmakta olan), ve ne zaman bir eşleşme bulunduğunda sonuç bayrağı ayarlanmış `true`. Son olarak, bir <xref:System.Activities.Validation.AssertValidation> sonuç bayrağı ayarlanmışsa bir doğrulama hatası oluşturmak için kullanılan `false`.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ContainmentValidation.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü oluşturun.  
  
3.  Programını başlatmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
