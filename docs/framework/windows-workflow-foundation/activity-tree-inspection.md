---
title: Etkinlik Ağacı Denetimi
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 692f36d993c3f9c27839122b388a24d0698a2b59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183035"
---
# <a name="activity-tree-inspection"></a>Etkinlik Ağacı Denetimi
Etkinlik ağacı denetimi, uygulama tarafından barındırılan iş akışlarını incelemek için iş akışı uygulaması yazarları tarafından kullanılır. Kullanarak, <xref:System.Activities.WorkflowInspectionServices>iş akışları belirli alt etkinlikler için aranabilir, bireysel etkinlikler ve özellikleri numaralandırılabilir ve etkinliklerin çalışma zamanı meta verileri belirli bir zamanda önbelleğe alınabilir. Bu konu, bir <xref:System.Activities.WorkflowInspectionServices> etkinlik ağacını incelemek için nasıl kullanılacağına genel bir bakış sağlar.  
  
## <a name="using-workflowinspectionservices"></a>İş AkışıDenetim Hizmetlerini Kullanma  
 Yöntem, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> belirtilen etkinlik ağacındaki tüm etkinlikleri sayısallandırmak için kullanılır. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>çocuklar, temsilci işleyicileri, değişken varsayılanlar ve bağımsız değişken ifadeleri de dahil olmak üzere ağaç içindeki tüm etkinliklere dokunan bir sayısal döndürür. Aşağıdaki örnekte, bir iş akışı tanımı <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While> <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>, , ve ifadeler kullanılarak oluşturulur. İş akışı tanımı oluşturulduktan sonra çağrılır `InspectActivity` ve yöntem çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Etkinlikleri sayısallandırmak için, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> kök etkinliği ve yine her döndürülen etkinlikte özyinelemeli olarak çağrılır. Aşağıdaki örnekte, <xref:System.Activities.Activity.DisplayName%2A> etkinlik ağacındaki her etkinlik ve ifadenin konsoluna yazılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Bu örnek kod aşağıdaki çıktıyı sağlar.  
  
 **Liste Öğesi 1**  
**Liste Öğesi 2**
**Liste Madde 3**
**Liste Madde 4**
**Liste Madde 5**
**Toplama eklenen öğeler.** 
 **Sıralı** **<\<Liste Dize>>**  
 **Süre**  
 **AddToCollection\<String>**  
 **VariableValue<\<ICollection String>>**  
 **LambdaValue\<String>**  
 **LocationReferenceValue<\<Liste String>>**  
 **LambdaValue\<Boolean>**  
 **LocationReferenceValue<\<Liste String>>**  
 **ForEach\<String>**  
 **VariableValue<Numaralandırıcı\<Dize>>**  
 **WriteLine**  
 **TemsilciBağımsız\<DeğişkenDeğer Dize>**  
 **Sequence**  
 **WriteLine**  
 **Literal\<String>** Tüm etkinlikleri <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> numaralandırmak yerine belirli bir etkinliği almak için kullanılır. Her <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> ikisi de ve `WorkflowInspectionServices.CacheMetadata` daha önce çağrılmadı ysa meta veri önbelleğe gerçekleştirin. Çağrıldıysa, <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> varolan meta verileri temel alınarak kullanılır. Bu nedenle, son çağrıdan bu yana <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> ağaç değişiklikleri yapıldıysa, beklenmeyen sonuçlar verebilir. Aramadan <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>sonra iş akışında değişiklikler yapıldıysa, meta veriler <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> yöntem çağırılarak yeniden önbelleğe alınabilir. Önbelleğe alma meta verileri sonraki bölümde ele alınmıştır.  
  
### <a name="caching-metadata"></a>Meta verileri önbelleğe alma  
 Bir etkinlik için meta verileri önbelleğe alma, etkinliğin bağımsız değişkenlerinin, değişkenlerinin, alt etkinliklerinin ve etkinlik temsilcilerinin açıklamasını oluşturur ve doğrular. Meta veriler, varsayılan olarak, bir etkinlik yürütme için hazırlandığında çalışma süresine göre önbelleğe alır. İş akışı ana bilgisayar yazarı bundan önce bir etkinlik veya etkinlik ağacı için meta verileri önbelleğe <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> almak isterse, örneğin tüm maliyeti peşin almak için, meta verileri istediğiniz zamanda önbelleğe almak için kullanılabilir.
