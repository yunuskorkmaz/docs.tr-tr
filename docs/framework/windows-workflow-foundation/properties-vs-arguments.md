---
title: "Özellikler vs. Arguments"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b3f06cf91591a373550f876f7b2111159067ba3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="properties-vs-arguments"></a>Özellikler vs. Arguments
Etkinliğin içinde veri geçirmek için kullanılabilir birkaç seçeneğiniz vardır. Kullanmanın yanı sıra <xref:System.Activities.InArgument>, etkinlikleri de geliştirilebilir standart CLR özellikleri ya da ortak kullanarak verileri alan <xref:System.Activities.ActivityAction> özellikleri. Bu konuda uygun yöntemi türü seçme anlatılmaktadır.  
  
## <a name="using-clr-properties"></a>CLR özelliklerini kullanma  
 Verileri activity içine geçirirken, CLR (kullanımı almak ve veri kullanıma sunmak için yordamları ayarlamak diğer bir deyişle, genel yöntemler) en kısıtlamaları olan seçeneği özelliklerdir. Çözüm derlendiğinde bir CLR özelliğine geçirilen parametre değerini bilinmesi gerekir; Bu değer iş akışı, her örneği için aynı olacaktır. Bu şekilde, bir CLR özelliğine geçirilen bir değer kod içinde tanımlanan bir sabit benzer; Bu değer, etkinlik süresince değiştiremezsiniz ve etkinlik farklı örnekleri için değiştirilemez. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>etkinlik tarafından kullanıma sunulan bir CLR özellik örneğidir; etkinliği çağırır yöntem adı çalışma zamanı koşullara göre değiştirilemez ve etkinliği her örneği için aynı olacaktır.  
  
## <a name="using-arguments"></a>Bağımsız değişkenleri kullanma  
 Verileri yalnızca bir kez etkinlik ömrü boyunca değerlendirildiğinde bağımsız değişkenleri kullanılmalıdır; diğer bir deyişle, değerini etkinlik ömrü boyunca değiştirmez ancak değer etkinlik farklı örnekleri için farklı olabilir. <xref:System.Activities.Statements.If.Condition%2A>bir kez hesaplanan bir değer örneğidir; Bu nedenle bu bağımsız değişken olarak tanımlanır. <xref:System.Activities.Statements.WriteLine.Text%2A>başka bir örneği yalnızca bir kez etkinliğin yürütme sırasında değerlendirilen bu yana bir bağımsız değişken olarak tanımlanan bir yöntemi, ancak etkinlik farklı örnekleri için farklı olabilir.  
  
## <a name="using-activityaction"></a>ActivityAction kullanma  
 Birden çok kez ömrü bir etkinliğin yürütme sırasında değerlendirilecek verileri gerektiğinde bir <xref:System.Activities.ActivityAction> kullanılmalıdır. Örneğin, <xref:System.Activities.Statements.While.Condition%2A> özelliği her bir yineleme değerlendirildiği <xref:System.Activities.Statements.While> döngü. Varsa bir <xref:System.Activities.InArgument> döngü bu amaç için hiçbir zaman bağımsız değişkeni için her bir yineleme reevaluated değil ve her zaman misiniz çıkış döndürebildiği aynı sonucu kullanıldı.
