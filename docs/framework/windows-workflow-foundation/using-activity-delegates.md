---
title: Etkinlik Temsilcileri Kullanma
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 8c9d82f47f709a89455f41691526b6ac9718a01f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004620"
---
# <a name="using-activity-delegates"></a>Etkinlik Temsilcileri Kullanma
Etkinlik temsilcileri kullanıcılar etkinliğin etkinlik tabanlı işleyicileri sağlayabilir, belirli bir imzaya sahip geri çağırmalar etkinlik yazarlar etkinleştirin. İki tür etkinlik temsilcileri kullanılabilir: <xref:System.Activities.ActivityAction%601> bir dönüş değeri olmayan etkinlik temsilcileri tanımlamak için kullanılır ve <xref:System.Activities.ActivityFunc%601> dönüş değerine sahip etkinlik temsilcileri tanımlamak için kullanılır.

Etkinlik temsilcileri için belirli bir imzaya sahip bir alt etkinlik burada kısıtlanmalıdır senaryolarda yararlıdır. Örneğin, bir <xref:System.Activities.Statements.While> etkinlik hiçbir kısıtlama olmadan alt etkinlik herhangi bir türde ancak gövdesinin içerebilir bir <xref:System.Activities.Statements.ForEach%601> etkinliği bir <xref:System.Activities.ActivityAction%601>ve sonuçta tarafından yürütülen bir alt etkinlik <xref:System.Activities.Statements.ForEach%601> olmalıdır bir <xref:System.Activities.InArgument%601> , koleksiyonun üyeleri aynı türü, <xref:System.Activities.Statements.ForEach%601> numaralandırır.

## <a name="using-activityaction"></a>ActivityAction kullanma

Birkaç [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] etkinlikler kullanma etkinlik eylemleri gibi <xref:System.Activities.Statements.Catch> etkinlik ve <xref:System.Activities.Statements.ForEach%601> etkinlik. Her durumda, etkinlik eylem burada Bu etkinliklerden birini kullanarak bir iş akışı oluştururken istenen davranışı sağlamak için bir etkinlik iş akışı yazarını belirtir bir konumu temsil eder. Aşağıdaki örnekte, bir <xref:System.Activities.Statements.ForEach%601> etkinliği konsol penceresine metin görüntülemek için kullanılır. Gövdesi <xref:System.Activities.Statements.ForEach%601> kullanılarak belirtilen bir <xref:System.Activities.ActivityAction%601> türü ile eşleşen <xref:System.Activities.Statements.ForEach%601> dizesi olduğu. <xref:System.Activities.Statements.WriteLine> Etkinlik belirtilen <xref:System.Activities.ActivityDelegate.Handler%2A> sahip kendi <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni dize değerleri koleksiyondaki bağlı olan <xref:System.Activities.Statements.ForEach%601> etkinlik yinelenir.

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument WriteLine koleksiyondaki bireysel öğeleri akış için kullanılır. İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.

```
HelloWorld.
```

Bu konudaki örnekleri nesne başlatma söz dizimi kullanın. Nesne başlatma söz dizimi etkinlikleri arasındaki ilişkiyi gösterir ve iş akışındaki etkinliklerin hiyerarşik bir görünümü sağlar çünkü kod içinde iş akışı tanımları oluşturma için kullanışlı bir yol olabilir. Nesne başlatma söz dizimi programlı olarak iş akışları oluşturduğunuzda kullanılacak gereksinimi yoktur. Aşağıdaki örnek önceki örneğe işlevsel olarak eşdeğerdir.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir oluşturucu çağırmaya gerek kalmadan nesneleri başlatma (C# Programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkId=161015) ve [nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme](https://go.microsoft.com/fwlink/?LinkId=161016).

Aşağıdaki örnekte, bir <xref:System.Activities.Statements.TryCatch> etkinliği, bir iş akışında kullanılır. Bir <xref:System.ApplicationException> iş akışı tarafından oluşturulur ve tarafından işlenen bir <xref:System.Activities.Statements.Catch%601> etkinlik. İşleyici için <xref:System.Activities.Statements.Catch%601> etkinliğin etkinlik eylemi bir <xref:System.Activities.Statements.WriteLine> etkinliği ve özel durum ayrıntısı aktarılan aracılığıyla kullanarak `ex` <xref:System.Activities.DelegateInArgument%601>.

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Ne zaman tanımlayan özel bir etkinlik oluşturma bir <xref:System.Activities.ActivityAction%601>, kullanmak bir <xref:System.Activities.Statements.InvokeAction%601> çağırmayı, model <xref:System.Activities.ActivityAction%601>. Bu örnekte, özel bir `WriteLineWithNotification` etkinlik tanımlanır. Bu etkinlik oluşan bir <xref:System.Activities.Statements.Sequence> içeren bir <xref:System.Activities.Statements.WriteLine> etkinliği tarafından izlenen bir <xref:System.Activities.Statements.InvokeAction%601> , çağıran bir <xref:System.Activities.ActivityAction%601> bir dize bağımsız değişkeni almayan.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Bir iş akışı oluşturulduğunda kullanarak `WriteLineWithNotification` etkinlik, iş akışı Yazar etkinlik eylemin istenen özel mantığı belirtir <xref:System.Activities.ActivityDelegate.Handler%2A>. Bu örnekte, bir iş akışı kullanan oluşturulur `WriteLineWithNotification` etkinliği ve bir <xref:System.Activities.Statements.WriteLine> etkinlik olarak kullanılan <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

Birden çok genel sürümü vardır <xref:System.Activities.Statements.InvokeAction%601> ve <xref:System.Activities.ActivityAction%601> bir veya daha fazla bağımsız değişkenleri geçirme sağlanan.

## <a name="using-activityfunc"></a>ActivityFunc kullanma

<xref:System.Activities.ActivityAction%601> hiçbir sonuç değeri etkinliğinden olduğunda yararlıdır ve <xref:System.Activities.ActivityFunc%601> bir sonuç değeri döndürüldüğünde kullanılır. Ne zaman tanımlayan özel bir etkinlik oluşturma bir <xref:System.Activities.ActivityFunc%601>, kullanmak bir <xref:System.Activities.Expressions.InvokeFunc%601> çağırmayı, model <xref:System.Activities.ActivityFunc%601>. Aşağıdaki örnekte, bir `WriteFillerText` etkinlik tanımlanır. Dolgu metin sağlamak için bir <xref:System.Activities.Expressions.InvokeFunc%601> bir tamsayı bağımsız değişkeni alır ve bir dize sonucunu sahip belirtilir. Dolgu metin alındıktan sonra konsolunu kullanarak görüntülenir bir <xref:System.Activities.Statements.WriteLine> etkinlik.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Metin sağlamak için bir etkinlik bir alan kullanılmalıdır `int` bağımsız değişken ve bir dize sonucu vardır. Bu örnek gösterir bir `TextGenerator` bu gereksinimleri karşılayan bir etkinlik.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Kullanılacak `TextGenerator` etkinliğiyle `WriteFillerText` etkinliği şeklinde belirtin <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
