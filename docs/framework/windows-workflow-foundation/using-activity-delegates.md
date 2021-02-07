---
description: 'Hakkında daha fazla bilgi edinin: etkinlik temsilcileri kullanma'
title: Etkinlik Temsilcileri Kullanma
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 2570d32c275975b8bda34fab2ffd79a49b6a9c73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755089"
---
# <a name="using-activity-delegates"></a>Etkinlik Temsilcileri Kullanma

Etkinlik temsilcileri etkinlik yazarlarının, etkinlik kullanıcılarının etkinlik tabanlı işleyiciler sağlayabileceği belirli imzalara sahip geri çağırmaları kullanıma sunmasına olanak tanır. İki tür etkinlik temsilcisi mevcuttur: <xref:System.Activities.ActivityAction%601> bir dönüş değeri olmayan etkinlik temsilcilerini tanımlamak için kullanılır ve <xref:System.Activities.ActivityFunc%601> dönüş değeri olan etkinlik temsilcilerini tanımlamak için kullanılır.

Etkinlik temsilcileri, bir alt etkinliğin belirli bir imzaya sahip olacak şekilde sınırlandırılmasının gerektiği senaryolarda faydalıdır. Örneğin, bir <xref:System.Activities.Statements.While> etkinlik herhangi bir kısıtlama olmadan herhangi bir alt etkinlik türünü içerebilir, ancak <xref:System.Activities.Statements.ForEach%601> etkinliğin gövdesi bir olur <xref:System.Activities.ActivityAction%601> ve tarafından son olarak yürütülen alt etkinliğin, <xref:System.Activities.Statements.ForEach%601> <xref:System.Activities.InArgument%601> numaralandırmalar tarafından koleksiyonun üyesi olan aynı türde olması gerekir <xref:System.Activities.Statements.ForEach%601> .

## <a name="using-activityaction"></a>ActivityAction kullanma

Etkinlik [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ve etkinlik gibi çeşitli etkinlikler etkinlik eylemlerini kullanır <xref:System.Activities.Statements.Catch> <xref:System.Activities.Statements.ForEach%601> . Her durumda etkinlik eylemi, iş akışı yazarının, bu etkinliklerden birini kullanarak bir iş akışı oluştururken istenen davranışı sağlamak için bir etkinlik belirttiği bir konumu temsil eder. Aşağıdaki örnekte, <xref:System.Activities.Statements.ForEach%601> konsol penceresinde metin göstermek için bir etkinlik kullanılır. Gövdesi, dize olan <xref:System.Activities.Statements.ForEach%601> türüyle eşleşen bir kullanılarak belirtilir <xref:System.Activities.ActivityAction%601> <xref:System.Activities.Statements.ForEach%601> . <xref:System.Activities.Statements.WriteLine>Öğesinde belirtilen etkinliğin <xref:System.Activities.ActivityDelegate.Handler%2A> <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni, etkinliğin yineleme koleksiyonundaki dize değerlerine bağımlıdır <xref:System.Activities.Statements.ForEach%601> .

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument, koleksiyondaki tek tek öğeleri WriteLine öğesine akışa almak için kullanılır. İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.

```console
HelloWorld.
```

Bu konudaki örnekler, nesne başlatma sözdizimini kullanır. Nesne başlatma sözdizimi, iş akışındaki etkinliklerin hiyerarşik bir görünümünü sağladığından koddaki iş akışı tanımlarını oluşturmak için kullanışlı bir yol olabilir ve etkinlikler arasındaki ilişkiyi gösterir. Program aracılığıyla iş akışları oluştururken nesne başlatma söz dizimini kullanma gereksinimi yoktur. Aşağıdaki örnek, önceki örneğe işlevsel olarak eşdeğerdir.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Oluşturucu çağrılmadan nesneleri başlatma (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) ve [nasıl yapılır: nesne Başlatıcısı kullanarak nesne bildirme (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).

Aşağıdaki örnekte, bir <xref:System.Activities.Statements.TryCatch> etkinlik bir iş akışında kullanılır. Bir <xref:System.ApplicationException> iş akışı tarafından oluşturulur ve bir etkinlik tarafından işlenir <xref:System.Activities.Statements.Catch%601> . <xref:System.Activities.Statements.Catch%601>Etkinliğin etkinlik eylemi için olan işleyici bir <xref:System.Activities.Statements.WriteLine> etkinliktir ve özel durum ayrıntısı, kullanılarak ile arasında akıtıdır `ex` <xref:System.Activities.DelegateInArgument%601> .

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Öğesini tanımlayan özel bir etkinlik oluştururken bunun <xref:System.Activities.ActivityAction%601> <xref:System.Activities.Statements.InvokeAction%601> çağrılmasını modellemek için kullanın <xref:System.Activities.ActivityAction%601> . Bu örnekte, özel bir `WriteLineWithNotification` etkinlik tanımlanmıştır. Bu etkinlik, bir <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> etkinliğin ve bir <xref:System.Activities.Statements.InvokeAction%601> <xref:System.Activities.ActivityAction%601> dize bağımsız değişkeni alan öğesini çağıran bir etkinlik içeren bir öğesinden oluşur.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Etkinlik kullanılarak bir iş akışı oluşturulduğunda `WriteLineWithNotification` , iş akışı yazarı etkinlik eyleminde istenen özel mantığı belirtir <xref:System.Activities.ActivityDelegate.Handler%2A> . Bu örnekte, etkinliğini kullanan bir iş akışı oluşturulur `WriteLineWithNotification` ve <xref:System.Activities.Statements.WriteLine> olarak bir etkinlik kullanılır <xref:System.Activities.ActivityDelegate.Handler%2A> .

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

' Nin birden çok genel sürümü vardır <xref:System.Activities.Statements.InvokeAction%601> ve <xref:System.Activities.ActivityAction%601> bir veya daha fazla bağımsız değişken geçirmek için sağlanır.

## <a name="using-activityfunc"></a>ActivityFunc kullanma

<xref:System.Activities.ActivityAction%601> etkinlikten sonuç değeri olmadığında yararlıdır ve <xref:System.Activities.ActivityFunc%601> bir sonuç değeri döndürüldüğünde kullanılır. Öğesini tanımlayan özel bir etkinlik oluştururken bunun <xref:System.Activities.ActivityFunc%601> <xref:System.Activities.Expressions.InvokeFunc%601> çağrılmasını modellemek için kullanın <xref:System.Activities.ActivityFunc%601> . Aşağıdaki örnekte bir `WriteFillerText` etkinlik tanımlanmıştır. Dolgu metnini sağlamak için, bir <xref:System.Activities.Expressions.InvokeFunc%601> tamsayı bağımsız değişkeni alan ve bir dize sonucu içeren bir belirtildi. Dolgu metni alındıktan sonra, bir etkinlik kullanılarak konsola görüntülenir <xref:System.Activities.Statements.WriteLine> .

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Metni sağlamak için bir etkinliğin bir `int` bağımsız değişken alan ve bir dize sonucu olan bir etkinlik kullanılması gerekir. Bu örnek `TextGenerator` , bu gereksinimleri karşılayan bir etkinlik gösterir.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Etkinliği `TextGenerator` etkinliğiyle birlikte kullanmak için, `WriteFillerText` öğesini olarak belirtin <xref:System.Activities.ActivityDelegate.Handler%2A> .

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
