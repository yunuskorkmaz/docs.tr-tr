---
title: Etkinlik Temsilcileri Kullanma
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: cbcc8f8e498be4f79f8fed5af7cd3557d7c55981
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837577"
---
# <a name="using-activity-delegates"></a>Etkinlik Temsilcileri Kullanma
Etkinlik temsilcileri etkinlik yazarlarının, etkinlik kullanıcılarının etkinlik tabanlı işleyiciler sağlayabileceği belirli imzalara sahip geri çağırmaları kullanıma sunmasına olanak tanır. İki tür etkinlik temsilcisi mevcuttur: <xref:System.Activities.ActivityAction%601>, dönüş değeri olmayan etkinlik temsilcilerini tanımlamak için kullanılır ve bir dönüş değeri olan etkinlik temsilcilerini tanımlamak için <xref:System.Activities.ActivityFunc%601> kullanılır.

Etkinlik temsilcileri, bir alt etkinliğin belirli bir imzaya sahip olacak şekilde sınırlandırılmasının gerektiği senaryolarda faydalıdır. Örneğin, bir <xref:System.Activities.Statements.While> etkinliği hiçbir kısıtlama olmadan herhangi bir alt etkinlik türünü içerebilir, ancak bir <xref:System.Activities.Statements.ForEach%601> etkinliğinin gövdesi bir <xref:System.Activities.ActivityAction%601>ve sonuçta <xref:System.Activities.Statements.ForEach%601> tarafından yürütülen alt etkinliğin, <xref:System.Activities.InArgument%601> numaralandırdığından koleksiyonun üyesi olan bir <xref:System.Activities.Statements.ForEach%601> sahip olması gerekir.

## <a name="using-activityaction"></a>ActivityAction kullanma

Çeşitli [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] etkinlikler, <xref:System.Activities.Statements.Catch> etkinliği ve <xref:System.Activities.Statements.ForEach%601> etkinliği gibi etkinlik eylemlerini kullanır. Her durumda etkinlik eylemi, iş akışı yazarının, bu etkinliklerden birini kullanarak bir iş akışı oluştururken istenen davranışı sağlamak için bir etkinlik belirttiği bir konumu temsil eder. Aşağıdaki örnekte, konsol penceresinde metin göstermek için bir <xref:System.Activities.Statements.ForEach%601> etkinliği kullanılır. <xref:System.Activities.Statements.ForEach%601> gövdesi, dize olan <xref:System.Activities.Statements.ForEach%601> türüyle eşleşen bir <xref:System.Activities.ActivityAction%601> kullanılarak belirtilir. <xref:System.Activities.ActivityDelegate.Handler%2A> belirtilen <xref:System.Activities.Statements.WriteLine> etkinliğinin <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni koleksiyondaki <xref:System.Activities.Statements.ForEach%601> etkinliğinin yineleme olan dize değerlerine bağımlıdır.

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

ActionArgument, koleksiyondaki tek tek öğeleri WriteLine öğesine akışa almak için kullanılır. İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.

```console
HelloWorld.
```

Bu konudaki örnekler, nesne başlatma sözdizimini kullanır. Nesne başlatma sözdizimi, iş akışındaki etkinliklerin hiyerarşik bir görünümünü sağladığından koddaki iş akışı tanımlarını oluşturmak için kullanışlı bir yol olabilir ve etkinlikler arasındaki ilişkiyi gösterir. Program aracılığıyla iş akışları oluştururken nesne başlatma söz dizimini kullanma gereksinimi yoktur. Aşağıdaki örnek, önceki örneğe işlevsel olarak eşdeğerdir.

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir Oluşturucu çağırılmadan nesneleri başlatmaC# (Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) ve [nasıl yapılır: nesne başlatıcısı kullanarak nesne bildirme (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).

Aşağıdaki örnekte, bir iş akışında <xref:System.Activities.Statements.TryCatch> etkinliği kullanılır. Bir <xref:System.ApplicationException> iş akışı tarafından oluşturulur ve bir <xref:System.Activities.Statements.Catch%601> etkinliği tarafından işlenir. <xref:System.Activities.Statements.Catch%601> etkinliğin etkinlik eyleminin işleyicisi bir <xref:System.Activities.Statements.WriteLine> etkinliğidir ve özel durum ayrıntısı `ex` <xref:System.Activities.DelegateInArgument%601>kullanılarak bu şekilde gönderilir.

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Bir <xref:System.Activities.ActivityAction%601>tanımlayan özel bir etkinlik oluştururken, bu <xref:System.Activities.ActivityAction%601>çağrılmasını modellemek için bir <xref:System.Activities.Statements.InvokeAction%601> kullanın. Bu örnekte, özel bir `WriteLineWithNotification` etkinliği tanımlanmıştır. Bu etkinlik, bir <xref:System.Activities.Statements.WriteLine> etkinliği ve ardından bir dize bağımsız değişkeni alan <xref:System.Activities.ActivityAction%601> çağıran bir <xref:System.Activities.Statements.InvokeAction%601> içeren bir <xref:System.Activities.Statements.Sequence> oluşur.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Bir iş akışı `WriteLineWithNotification` etkinliği kullanılarak oluşturulduğunda, iş akışı yazarı etkinlik eyleminin <xref:System.Activities.ActivityDelegate.Handler%2A>istenen özel mantığı belirler. Bu örnekte, `WriteLineWithNotification` etkinliğini kullanan bir iş akışı oluşturulur ve <xref:System.Activities.ActivityDelegate.Handler%2A>olarak <xref:System.Activities.Statements.WriteLine> etkinliği kullanılır.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

<xref:System.Activities.Statements.InvokeAction%601> birden çok genel sürümü vardır ve bir veya daha fazla bağımsız değişkeni geçirmek için <xref:System.Activities.ActivityAction%601> sağlanır.

## <a name="using-activityfunc"></a>ActivityFunc kullanma

<xref:System.Activities.ActivityAction%601>, etkinlikten sonuç değeri olmadığında faydalıdır ve bir sonuç değeri döndürüldüğünde <xref:System.Activities.ActivityFunc%601> kullanılır. Bir <xref:System.Activities.ActivityFunc%601>tanımlayan özel bir etkinlik oluştururken, bu <xref:System.Activities.ActivityFunc%601>çağrılmasını modellemek için bir <xref:System.Activities.Expressions.InvokeFunc%601> kullanın. Aşağıdaki örnekte, bir `WriteFillerText` etkinliği tanımlanmıştır. Dolgu metnini sağlamak için, bir tamsayı bağımsız değişkeni alan ve bir dize sonucu olan bir <xref:System.Activities.Expressions.InvokeFunc%601> belirtilir. Dolgu metni alındıktan sonra, <xref:System.Activities.Statements.WriteLine> bir etkinlik kullanılarak konsola görüntülenir.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Metni sağlamak için bir etkinliğin bir `int` bağımsız değişken alan ve bir dize sonucu olan bir etkinlik kullanılması gerekir. Bu örnek, bu gereksinimleri karşılayan bir `TextGenerator` etkinliğini gösterir.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

`TextGenerator` etkinliğini `WriteFillerText` etkinliğiyle kullanmak için, <xref:System.Activities.ActivityDelegate.Handler%2A>olarak belirtin.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
