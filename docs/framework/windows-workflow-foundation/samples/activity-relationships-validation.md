---
title: Etkinlik ilişkilerini doğrulama
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098951"
---
# <a name="activity-relationships-validation"></a>Etkinlik ilişkilerini doğrulama
Bu örnek üç etkinliklerden, oluşur `CreateCity`, `CreateState`, ve `CreateCountry`. `CreateCity` içinde olmalıdır bir `CreateState` etkinliği ve `CreateState` içinde olmalıdır bir `CreateCountry` etkinlik. Bu örnek amacıyla kod için doğrulama mantığını bulunduğu `CreateState` etkinliği ve XAML için `CreateCity` etkinlik. Her iki kısıtlamaları aynı davranışa sahip.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Etkinlikleri arasındaki ilişkileri doğrulamak Geliştirici izin veren aşağıdaki üç Yardımcısı etkinlikleri sağlar:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Geçerli düğümünün üst öğeye ait tüm etkinliklerin toplanmasını sağlar  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Geçerli düğüm hariç geçerli düğüm, alt ağacına ait tüm etkinliklerin toplanmasını sağlar  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Geçerli düğüm aynı ağacındaki tüm etkinlikleri koleksiyonunu sağlar  
  
 Örnekte, bir <xref:System.Activities.Statements.ForEach%601> etkinlik tarafından döndürülen bir koleksiyonda rehberlik için kullanılan <xref:System.Activities.Validation.GetParentChain>. Türü karşılaştırılır koleksiyondaki her öğe için `CreateCountry` (veya `CreateState` varsa `CreateCity` Doğrulanmakta olan), ve ne zaman bir eşleşme bulunursa sonuç bayrağı ayarlandığında `true`. Son olarak, bir <xref:System.Activities.Validation.AssertValidation> sonucu bayrağı ayarlanmışsa bir doğrulama hatası oluşturmak için kullanılan `false`.  
  
### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ContainmentValidation.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü oluşturun.  
  
3.  Programını başlatmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
