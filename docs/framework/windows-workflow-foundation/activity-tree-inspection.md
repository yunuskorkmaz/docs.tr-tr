---
description: 'Daha fazla bilgi edinin: Etkinlik ağacı denetimi'
title: Etkinlik Ağacı Denetimi
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: aac19dd99199481e6ad0d1a554ad1846678c160e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787961"
---
# <a name="activity-tree-inspection"></a>Etkinlik Ağacı Denetimi

Etkinlik ağacı incelemesi, iş akışı uygulama yazarları tarafından, uygulama tarafından barındırılan iş akışlarını incelemek için kullanılır. Kullanarak <xref:System.Activities.WorkflowInspectionServices> , iş akışları belirli alt etkinlikler için aranabilir, bireysel etkinlikler ve bunların özellikleri listelenebilir ve etkinliklerin çalışma zamanı meta verileri belirli bir zamanda önbelleğe alınabilir. Bu konu, bir genel bakış <xref:System.Activities.WorkflowInspectionServices> ve bir etkinlik ağacını denetlemek için nasıl kullanılacağını sağlar.  
  
## <a name="using-workflowinspectionservices"></a>Workflowwınspectionservices kullanma  

 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>Yöntemi, belirtilen etkinlik ağacındaki tüm etkinlikleri listelemek için kullanılır. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> ağaç içinde alt öğeler, temsilci işleyicileri, değişken Varsayılanları ve bağımsız değişken ifadeleri dahil tüm etkinliklere dokunan bir numaralandırılabilir döndürür. Aşağıdaki örnekte, bir iş akışı tanımı,,,, <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.While> <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.Statements.WriteLine> ve ifadeleri kullanılarak oluşturulur. İş akışı tanımı oluşturulduktan sonra, çağrılır ve sonra `InspectActivity` yöntemi çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Etkinlikleri numaralandırmak için, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> kök etkinlik üzerinde çağrılır ve döndürülen her etkinlik üzerinde yinelemeli olarak yeniden özyinelemeli olur. Aşağıdaki örnekte, <xref:System.Activities.Activity.DisplayName%2A> etkinlik ağacındaki her etkinlik ve ifade konsola yazılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Bu örnek kod aşağıdaki çıktıyı sağlar.  
  
 **Liste öğesi 1**  
**Liste öğesi 2** 
 **Liste öğesi 3** 
 **Liste öğesi 4** 
 **Liste öğesi 5** 
 **Koleksiyona eklenen öğeler.** 
 **Dizi** **sabit değer<\<String> > listesi**  
 **Edilirken**  
 **AddToCollection\<String>**  
 **VariableValue<ICollection\<String>>**  
 **Lambdadvalue\<String>**  
 **LocationReferenceValue<listesi\<String>>**  
 **Lambdadvalue\<Boolean>**  
 **LocationReferenceValue<listesi\<String>>**  
 **ForEach\<String>**  
 **VariableValue<IEnumerable\<String>>**  
 **WriteLine**  
 **DelegateArgumentValue\<String>**  
 **Sequence**  
 **WriteLine**  
 **Değişmez \<String> değer**  Tüm etkinlikleri listelemek yerine belirli bir etkinliği almak için <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> kullanılır. Hem hem de <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> `WorkflowInspectionServices.CacheMetadata` daha önce çağrılmayan meta veri önbelleğe alma işlemi gerçekleştirin. <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>Çağrılırsa, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> mevcut meta verileri temel alır. Bu nedenle, son çağrısından sonra ağaç değişiklikleri yapılmışsa <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> , <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> beklenmedik sonuçlara neden olabilir. Çağrıldıktan sonra iş akışında değişiklik yapılmışsa <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> meta veriler, yöntemi çağırarak yeniden önbelleğe alınabilir <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> . Önbelleğe alma meta verileri, sonraki bölümde ele alınmıştır.  
  
### <a name="caching-metadata"></a>Önbelleğe alma meta verileri  

 Bir etkinliğin meta verilerinin önbelleğe alınması, etkinliğin bağımsız değişkenlerinin, değişkenlerinin, alt etkinliklerinin ve etkinlik temsilcilerinin bir açıklamasını oluşturur ve doğrular. Varsayılan olarak meta veriler, bir etkinlik yürütmeye hazırlandığı zaman çalışma zamanı tarafından önbelleğe alınır. Bir iş akışı ana bilgisayar yazarı, bundan önce bir etkinlik veya etkinlik ağacının meta verilerini önbelleğe almak istiyorsa (örneğin, tüm maliyeti kapladıysanız), <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> meta verileri istenen zamanda önbelleğe almak için kullanılabilir.
