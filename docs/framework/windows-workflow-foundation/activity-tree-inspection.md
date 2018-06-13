---
title: Etkinlik ağaç denetleme
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 4f2ca6bff27cfe0e3362e2a3b95cd08a0f8d5297
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516847"
---
# <a name="activity-tree-inspection"></a>Etkinlik ağaç denetleme
Etkinlik ağaç denetleme, uygulama tarafından barındırılan iş akışları incelemek için iş akışı uygulama yazarlar tarafından kullanılır. Kullanarak <xref:System.Activities.WorkflowInspectionServices>iş akışları etkinlikler belirli alt etkinlikler için arama ve bunların özelliklerini olarak numaralandırılmış ve etkinliklerin çalışma zamanı meta verileri, belirli bir süre boyunca önbelleğe alınacağını. Bu konu genel bir bakış sağlar <xref:System.Activities.WorkflowInspectionServices> ve bir etkinlik ağacı incelemek için kullanma.  
  
## <a name="using-workflowinspectionservices"></a>WorkflowInspectionServices kullanma  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Yöntemi belirtilen etkinlik ağacında etkinliklerin tümünü numaralandırmak için kullanılır. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> alt öğe, temsilci işleyicileri, değişkeni varsayılan ve bağımsız değişkeni ifadeler gibi ağaç içindeki tüm etkinlikleri dokunur bir sayıyı döndürür. Aşağıdaki örnekte, bir iş akışı tanımı kullanılarak oluşturulan bir <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>ve ifadeler. İş akışı tanımı oluşturulduktan sonra çağrılır ve ardından `InspectActivity` yöntemi çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Etkinlikler Numaralandırılacak <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Kök etkinlik ve yeniden döndürülen her etkinlik yinelemeli olarak adlandırılır. Aşağıdaki örnekte, <xref:System.Activities.Activity.DisplayName%2A> her bir etkinlik ve etkinlik ifadesinde ağaç konsoluna yazılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Bu örnek kod, aşağıdaki çıkış sağlar.  
  
 **Liste öğesi 1**  
**Liste öğesi 2**   
**Liste öğesi 3**   
**Liste öğesi 4**   
**Liste öğesi 5**   
**Koleksiyona eklenen öğeler.**   
**Sırası**   
 **Değişmez değer < listesi\<dize >>**  
 **While**  
 **AddToCollection\<dize >**  
 **VariableValue < ICollection\<dize >>**  
 **LambdaValue\<dize >**  
 **LocationReferenceValue < listesi\<dize >>**  
 **LambdaValue\<Boole >**  
 **LocationReferenceValue < listesi\<dize >>**  
 **ForEach\<dize >**  
 **VariableValue < IEnumerable\<dize >>**  
 **WriteLine**  
 **DelegateArgumentValue\<dize >**  
 **Sırası**  
 **WriteLine**  
 **Değişmez değer\<dize >** tüm etkinlikleri numaralandırma yerine belirli bir etkinliğe almak için <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> kullanılır. Her ikisi de <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> ve <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> , meta verileri önbelleğe alma işlemi `WorkflowInspectionServices.CacheMetadata` daha önce çağrılmadıysa. Varsa <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> sonra adlı <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> varolan meta verileri temel alarak. Bu nedenle, son çağrısından sonra ağaç değişiklik yapılıp yapılmadığını <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> beklenmeyen sonuçlar verebilir. İş akışına çağrıldıktan sonra yapılan değişiklikler, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, meta verileri yeniden önbelleğe alınacağını çağırarak <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> yöntemi. Önbelleğe alma meta verileri bir sonraki bölümde ele alınmıştır.  
  
### <a name="caching-metadata"></a>Meta verileri önbelleğe alma  
 Bir etkinlik için meta verileri önbelleğe alma oluşturur ve açıklamasını etkinliğe ilişkin bağımsız değişkenler, değişkenleri, alt etkinlikleri ve etkinlik temsilciler doğrular. Bir etkinlik yürütme için hazırlandığınızda meta verileri, varsayılan olarak, çalışma zamanı tarafından önbelleğe alınır. Bir etkinlik veya tüm maliyet önceden, ardından yapılacak Örneğin bu önce etkinlik ağacı için meta verileri önbelleğe almak bir iş akışı ana Yazar istiyorsa, <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> istenen zamanında meta verileri önbelleğe almak için kullanılabilir.
