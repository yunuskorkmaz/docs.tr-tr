---
title: Etkinlik Temsilcileri Kullanma
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 63f550549456404b237067c98afdb18a8758dd7a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989092"
---
# <a name="using-activity-delegates"></a>Etkinlik Temsilcileri Kullanma
Etkinlik temsilcileri etkinlik yazarlarının, etkinlik kullanıcılarının etkinlik tabanlı işleyiciler sağlayabileceği belirli imzalara sahip geri çağırmaları kullanıma sunmasına olanak tanır. İki tür etkinlik temsilcisi mevcuttur: <xref:System.Activities.ActivityAction%601> bir dönüş değeri olmayan etkinlik temsilcilerini tanımlamak için kullanılır ve <xref:System.Activities.ActivityFunc%601> dönüş değeri olan etkinlik temsilcilerini tanımlamak için kullanılır.

Etkinlik temsilcileri, bir alt etkinliğin belirli bir imzaya sahip olacak şekilde sınırlandırılmasının gerektiği senaryolarda faydalıdır. <xref:System.Activities.Statements.While> Örneğin, bir etkinlik hiçbir kısıtlama olmadan herhangi bir alt etkinlik türünü içerebilir, ancak <xref:System.Activities.ActivityAction%601> <xref:System.Activities.Statements.ForEach%601> etkinliğin gövdesi bir olur ve tarafından sonunda tarafından <xref:System.Activities.Statements.ForEach%601> yürütülen alt etkinliğin bir olması <xref:System.Activities.InArgument%601> gerekir , ' nin <xref:System.Activities.Statements.ForEach%601> numaralandıraldığı koleksiyon üyeleri türü.

## <a name="using-activityaction"></a>ActivityAction kullanma

Etkinlik [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Catch> ve etkinlik<xref:System.Activities.Statements.ForEach%601> gibi çeşitli etkinlikler etkinlik eylemlerini kullanır. Her durumda etkinlik eylemi, iş akışı yazarının, bu etkinliklerden birini kullanarak bir iş akışı oluştururken istenen davranışı sağlamak için bir etkinlik belirttiği bir konumu temsil eder. Aşağıdaki örnekte, konsol penceresinde metin <xref:System.Activities.Statements.ForEach%601> göstermek için bir etkinlik kullanılır. Gövdesi <xref:System.Activities.Statements.ForEach%601> , dize olan türüyle <xref:System.Activities.Statements.ForEach%601> eşleşen bir <xref:System.Activities.ActivityAction%601> kullanılarak belirtilir. Öğesinde belirtilen etkinliğin bağımsız değişkeni, <xref:System.Activities.Statements.ForEach%601> etkinliğin yineleme koleksiyonundaki dize değerlerine bağımlıdır. <xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.ActivityDelegate.Handler%2A>

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument, koleksiyondaki tek tek öğeleri WriteLine öğesine akışa almak için kullanılır. İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.

```console
HelloWorld.
```

Bu konudaki örnekler, nesne başlatma sözdizimini kullanır. Nesne başlatma sözdizimi, iş akışındaki etkinliklerin hiyerarşik bir görünümünü sağladığından koddaki iş akışı tanımlarını oluşturmak için kullanışlı bir yol olabilir ve etkinlikler arasındaki ilişkiyi gösterir. Program aracılığıyla iş akışları oluştururken nesne başlatma söz dizimini kullanma gereksinimi yoktur. Aşağıdaki örnek, önceki örneğe işlevsel olarak eşdeğerdir.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Nesne başlatıcıları hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir oluşturucuyu (C# Programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkId=161015) çağırmadan nesneleri başlatın ve [şunları yapın: Nesne Başlatıcısı](https://go.microsoft.com/fwlink/?LinkId=161016)kullanarak bir nesne bildirin.

Aşağıdaki örnekte, <xref:System.Activities.Statements.TryCatch> bir etkinlik bir iş akışında kullanılır. Bir <xref:System.ApplicationException> iş akışı tarafından oluşturulur ve bir <xref:System.Activities.Statements.Catch%601> etkinlik tarafından işlenir. <xref:System.Activities.Statements.Catch%601> Etkinliğin etkinlik eylemi için olan işleyici bir <xref:System.Activities.Statements.WriteLine> etkinliktir ve özel durum ayrıntısı, `ex` <xref:System.Activities.DelegateInArgument%601>kullanılarak ile arasında akıtıdır.

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

<xref:System.Activities.ActivityAction%601>Öğesini tanımlayan özel bir etkinlik oluştururken bunun çağrılmasını <xref:System.Activities.ActivityAction%601>modellemek <xref:System.Activities.Statements.InvokeAction%601> için kullanın. Bu örnekte, özel `WriteLineWithNotification` bir etkinlik tanımlanmıştır. <xref:System.Activities.Statements.Sequence> Bu etkinlik, bir <xref:System.Activities.Statements.WriteLine> etkinliğin ve <xref:System.Activities.Statements.InvokeAction%601> bir dize bağımsız değişkeni alan öğesini çağıran <xref:System.Activities.ActivityAction%601> bir etkinlik içeren bir öğesinden oluşur.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

`WriteLineWithNotification` Etkinlik kullanılarak bir iş akışı oluşturulduğunda, iş akışı yazarı etkinlik <xref:System.Activities.ActivityDelegate.Handler%2A>eyleminde istenen özel mantığı belirtir. Bu örnekte, `WriteLineWithNotification` etkinliğini kullanan bir iş akışı oluşturulur ve olarak bir <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.ActivityDelegate.Handler%2A>etkinlik kullanılır.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

' Nin <xref:System.Activities.Statements.InvokeAction%601> birden çok genel sürümü vardır <xref:System.Activities.ActivityAction%601> ve bir veya daha fazla bağımsız değişken geçirmek için sağlanır.

## <a name="using-activityfunc"></a>ActivityFunc kullanma

<xref:System.Activities.ActivityAction%601>etkinlikten sonuç değeri olmadığında yararlıdır ve <xref:System.Activities.ActivityFunc%601> bir sonuç değeri döndürüldüğünde kullanılır. <xref:System.Activities.ActivityFunc%601>Öğesini tanımlayan özel bir etkinlik oluştururken bunun çağrılmasını <xref:System.Activities.ActivityFunc%601>modellemek <xref:System.Activities.Expressions.InvokeFunc%601> için kullanın. Aşağıdaki örnekte bir `WriteFillerText` etkinlik tanımlanmıştır. Dolgu metnini sağlamak için, bir tamsayı <xref:System.Activities.Expressions.InvokeFunc%601> bağımsız değişkeni alan ve bir dize sonucu içeren bir belirtildi. Dolgu metni alındıktan sonra, bir <xref:System.Activities.Statements.WriteLine> etkinlik kullanılarak konsola görüntülenir.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Metni sağlamak için bir etkinliğin bir `int` bağımsız değişken alan ve bir dize sonucu olan bir etkinlik kullanılması gerekir. Bu örnek, bu `TextGenerator` gereksinimleri karşılayan bir etkinlik gösterir.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Etkinliği `TextGenerator` etkinliğiyle`WriteFillerText` birlikte kullanmak için, <xref:System.Activities.ActivityDelegate.Handler%2A>öğesini olarak belirtin.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
