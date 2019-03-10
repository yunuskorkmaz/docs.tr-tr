---
title: Etkinlik ağacı denetimi
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 014795b79b3536b387096e4de64266e26649da21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705499"
---
# <a name="activity-tree-inspection"></a>Etkinlik ağacı denetimi
Etkinlik ağacı denetimi, uygulama tarafından barındırılan iş akışları incelemek için iş akışı uygulama yazarları tarafından kullanılır. Kullanarak <xref:System.Activities.WorkflowInspectionServices>, iş akışları bireysel etkinlikler belirli alt etkinlikler için arama ve özelliklerini incelenebilen ve etkinliklerin çalışma zamanı meta verileri, belirli bir süre boyunca önbelleğe alınacağını. Bu konu, genel bir bakış sağlar. <xref:System.Activities.WorkflowInspectionServices> ve nasıl bir etkinlik ağacı denetlemek için kullanılır.  
  
## <a name="using-workflowinspectionservices"></a>WorkflowInspectionServices kullanma  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Yöntemi belirtilen etkinlik ağacında etkinliklerin tümünü listeleme için kullanılır. <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> alt öğeleri, temsilci işleyicileri, değişkeni varsayılan olarak ve bağımsız değişken ifadeleri gibi ağaç içindeki tüm etkinlikleri dokunduğu bir numaralandırılabilir döndürür. Aşağıdaki örnekte, bir iş akışı tanımı kullanılarak oluşturulan bir <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.WriteLine>ve ifadeler. İş akışı tanımı oluşturulduktan sonra çağrılır ve ardından `InspectActivity` yöntemi çağrılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 Etkinlikleri numaralandırma <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> Kök etkinlik ve yeniden yinelemeli olarak döndürülen her etkinlik üzerinde çağrılır. Aşağıdaki örnekte, <xref:System.Activities.Activity.DisplayName%2A> her etkinliği ve etkinlik ifade ağacı konsoluna yazılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 Bu örnek kod aşağıdaki çıkışı sağlar.  
  
 **Liste öğesi 1**  
**Liste öğesi 2**   
**Liste öğesi 3**   
**Liste öğesi 4**   
**Liste öğesi 5**   
**Koleksiyonuna eklediğiniz öğeleri.**   
**Dizisi**   
 **Değişmez değer < listesi\<dize >>**  
 **While**  
 **AddToCollection\<dizesi >**  
 **VariableValue < ICollection\<dize >>**  
 **LambdaValue\<dizesi >**  
 **LocationReferenceValue < listesi\<dize >>**  
 **LambdaValue\<Boole >**  
 **LocationReferenceValue < listesi\<dize >>**  
 **ForEach\<dizesi >**  
 **VariableValue < IEnumerable\<dize >>**  
 **WriteLine**  
 **DelegateArgumentValue\<dizesi >**  
 **Sequence**  
 **WriteLine**  
 **Değişmez değer\<dizesi >** tüm etkinlikleri numaralandırma yerine belirli bir etkinliğe alınacak <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> kullanılır. Her ikisi de <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> ve <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> , meta verileri önbelleğe alma işlemi `WorkflowInspectionServices.CacheMetadata` önceden çağrılmadıysa. Varsa <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> sonra çağırıldı <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> mevcut meta verileri temel alır. Bu nedenle, son çağrısından sonra ağaç değişiklikler yapılıp yapılmadığını <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>, <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> beklenmeyen sonuçlar verebilir. Çağırdıktan sonra iş akışı için değişiklikler yapılmışsa <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>, meta verileri yeniden önbelleğe alınacağını çağırarak <xref:System.Activities.Validation.ActivityValidationServices> <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> yöntemi. Önbelleğe alma meta verileri, sonraki bölümde ele alınmıştır.  
  
### <a name="caching-metadata"></a>Meta verileri önbelleğe alma  
 Bir etkinlik meta verilerini önbelleğe alma, oluşturur ve bir etkinliğin bağımsız değişkenler, değişkenleri, alt etkinlikleri ve etkinlik temsilcileri açıklamasını doğrular. Bir etkinlik yürütme için hazırlandığınızda meta verileri, varsayılan olarak, çalışma zamanı tarafından önbelleğe alınır. Bir etkinlik ya da bu, örneğin tüm maliyeti, ön maliyet, ardından yararlanmak önce etkinlik ağacı için meta verileri önbelleğe almak bir iş akışı konak Yazar istiyorsa, <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> istenen zaman meta verileri önbelleğe almak için kullanılabilir.
