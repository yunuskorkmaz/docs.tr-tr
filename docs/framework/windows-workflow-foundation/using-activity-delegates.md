---
title: Etkinlik temsilcileri kullanma
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 96a412a066342fb9c459e1388c5b58847ebac390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518958"
---
# <a name="using-activity-delegates"></a>Etkinlik temsilcileri kullanma
Etkinlik temsilciler etkinlik yazarların kullanıcılar etkinliğin etkinlik tabanlı işleyicileri sağlayabilir belirli imzaları ile geri çağırmalar etkinleştirin. İki tür etkinlik temsilciler kullanılabilir: <xref:System.Activities.ActivityAction%601> bir dönüş değeri olmayan etkinlik temsilciler tanımlamak için kullanılır ve <xref:System.Activities.ActivityFunc%601> bir dönüş değerine sahip etkinlik temsilciler tanımlamak için kullanılır.  
  
 Etkinlik Temsilciler, belirli bir imza sahibi için bir alt etkinlik burada kısıtlanmalıdır senaryolarda kullanışlıdır. Örneğin, bir <xref:System.Activities.Statements.While> etkinlik alt etkinlik hiçbir kısıtlamalarına sahip herhangi bir türde ancak gövdesini içerebilir bir <xref:System.Activities.Statements.ForEach%601> etkinliği bir <xref:System.Activities.ActivityAction%601>, sonuçta tarafından yürütülen alt etkinlik <xref:System.Activities.Statements.ForEach%601> olmalıdır bir <xref:System.Activities.InArgument%601> , koleksiyonun üyeleri aynı türde olduğundan, <xref:System.Activities.Statements.ForEach%601> numaralandırır.  
  
## <a name="using-activityaction"></a>ActivityAction kullanma  
 Birkaç [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] etkinlikleri etkinlik eylemler gibi kullanmak <xref:System.Activities.Statements.Catch> etkinlik ve <xref:System.Activities.Statements.ForEach%601> etkinlik. Her durumda, etkinlik eylem burada şu etkinliklerden birini kullanarak bir iş akışı oluştururken istenen davranışı sağlamak için bir etkinlik iş akışı yazarı belirtir bir konumu temsil eder. Aşağıdaki örnekte, bir <xref:System.Activities.Statements.ForEach%601> etkinlik konsol penceresine metni görüntülemek için kullanılır. Gövdesini <xref:System.Activities.Statements.ForEach%601> kullanılarak belirtilen bir <xref:System.Activities.ActivityAction%601> türü ile eşleşen <xref:System.Activities.Statements.ForEach%601> dize olduğu. <xref:System.Activities.Statements.WriteLine> Belirtilen etkinlik <xref:System.Activities.ActivityDelegate.Handler%2A> sahip kendi <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni bağlı koleksiyondaki dize değerleri, <xref:System.Activities.Statements.ForEach%601> etkinlik yineler.  
  
 [!code-csharp[CFX_ActivityExample#6](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]  
  
 ActionArgument WriteLine koleksiyon içindeki öğeleri akış için kullanılır. İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
 ``` 
 HelloWorld.
 ```  
Bu konudaki örnekler nesne başlatma sözdizimini kullanın. Nesne başlatma sözdizimi etkinlikleri arasındaki ilişkiyi gösterir ve iş akışındaki etkinliklerin hiyerarşik bir görünümü sağlar kodda iş akışı tanımları oluşturmak için kullanışlı bir yol olabilir. Program aracılığıyla iş akışları oluşturduğunuzda, nesne başlatma sözdizimi kullanma zorunluluğu yoktur. Aşağıdaki örnek önceki örneğe işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[CFX_ActivityExample#7](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]  
  
 Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Oluşturucusu (C# programlama Kılavuzu) çağırma olmadan nesneleri başlatma](http://go.microsoft.com/fwlink/?LinkId=161015) ve [nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
 Aşağıdaki örnekte, bir <xref:System.Activities.Statements.TryCatch> etkinlik, bir iş akışında kullanılır. Bir <xref:System.ApplicationException> iş akışı tarafından oluşturulan ve tarafından işlenen bir <xref:System.Activities.Statements.Catch%601> etkinlik. İşleyicisi <xref:System.Activities.Statements.Catch%601> etkinliğin etkinlik eylem bir <xref:System.Activities.Statements.WriteLine> etkinliği ve özel durum ayrıntısı aktarılan aracılığıyla kullanarak `ex` <xref:System.Activities.DelegateInArgument%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Ne zaman tanımlayan bir özel etkinlik oluşturma bir <xref:System.Activities.ActivityAction%601>, kullanan bir <xref:System.Activities.Statements.InvokeAction%601> , çağrılmasını modellemek için <xref:System.Activities.ActivityAction%601>. Bu örnekte, özel bir `WriteLineWithNotification` etkinlik tanımlanır. Bu etkinlik oluşan bir <xref:System.Activities.Statements.Sequence> içeren bir <xref:System.Activities.Statements.WriteLine> etkinlik arkasından bir <xref:System.Activities.Statements.InvokeAction%601> , çağıran bir <xref:System.Activities.ActivityAction%601> bir dize bağımsız değişkeni alır.  
  
 [!code-csharp[CFX_ActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]  
  
 Bir iş akışı oluşturulduğunda kullanarak `WriteLineWithNotification` etkinlik, iş akışı yazarı belirtir istenen Özel mantık etkinlik eylem <xref:System.Activities.ActivityDelegate.Handler%2A>. Bu örnekte, bir iş akışı kullanan oluşturulur `WriteLineWithNotification` etkinliği ve bir <xref:System.Activities.Statements.WriteLine> etkinlik olarak kullanılan <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]  
  
 Birden çok genel sürümü vardır <xref:System.Activities.Statements.InvokeAction%601> ve <xref:System.Activities.ActivityAction%601> bir veya daha fazla bağımsız değişkenleri geçirme sağlanan.  
  
## <a name="using-activityfunc"></a>ActivityFunc kullanma  
 <xref:System.Activities.ActivityAction%601> hiçbir sonuç değeri etkinliğinden olduğunda yararlıdır ve <xref:System.Activities.ActivityFunc%601> sonuç değeri döndürdüğünde kullanılır. Ne zaman tanımlayan bir özel etkinlik oluşturma bir <xref:System.Activities.ActivityFunc%601>, kullanan bir <xref:System.Activities.Expressions.InvokeFunc%601> , çağrılmasını modellemek için <xref:System.Activities.ActivityFunc%601>. Aşağıdaki örnekte, bir `WriteFillerText` etkinlik tanımlanır. Dolgu metin sağlamak için bir <xref:System.Activities.Expressions.InvokeFunc%601> bir tamsayı bağımsız değişken ve bir dizi sonuç sahip belirtilir. Dolgu metin alındıktan sonra konsol kullanmaya görüntülenir bir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
 [!code-csharp[CFX_ActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]  
  
 Metin sağlamak için bir etkinlik bir alan kullanılmalıdır `int` bağımsız değişkeni ve bir dizi sonuç sahiptir. Bu örnek gösteren bir `TextGenerator` bu gereksinimleri karşılayan etkinlik.  
  
 [!code-csharp[CFX_ActivityExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]  
  
 Kullanılacak `TextGenerator` etkinlikle `WriteFillerText` etkinliği olarak belirtmek <xref:System.Activities.ActivityDelegate.Handler%2A>.  
  
 [!code-csharp[CFX_ActivityExample#5](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ActivityActions’ı Kullanıma Sunma ve Çağırma](../../../docs/framework/windows-workflow-foundation/samples/exposing-and-invoking-activityactions.md)
