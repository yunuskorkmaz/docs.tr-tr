---
title: Özellikler ve Arguments
ms.date: 03/30/2017
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
ms.openlocfilehash: a6ea4755599f18e8bbaa8187941623578d2168ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962636"
---
# <a name="properties-vs-arguments"></a>Özellikler ve Arguments
Bir etkinlik içinde veri geçirmek için kullanılabilen birkaç seçeneğiniz vardır. Kullanmanın yanı sıra <xref:System.Activities.InArgument>, etkinlikleri de geliştirilebilir standart CLR özellikleri veya ortak kullanarak veri alması <xref:System.Activities.ActivityAction> özellikleri. Bu konuda, uygun bir yöntem türü seç anlatılmaktadır.  
  
## <a name="using-clr-properties"></a>CLR özelliklerini kullanma  
 Bir etkinlik içinde veri geçirirken, CLR Özellikleri (kullanımı alın ve verileri göstermek için yordamlar ayarlayın diğer bir deyişle, genel yöntemler) en kısıtlamaları olan seçenektir. Çözüm derlendiğinde bir CLR özelliği geçirilen parametrenin değeri bilinmesi gerekir; Bu değer, her iş akışı örneğiyle aynı olacaktır. Bu şekilde, bir değeri bir CLR özelliği geçirilen kod içinde tanımlanmış bir sabit benzer; Bu değer, etkinlik süresince değiştiremezsiniz ve etkinlik için farklı örnekleri değiştirilemez. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> bir etkinlik tarafından kullanıma sunulan bir CLR özellik örneğidir; Etkinlik çağıran yöntem adı üzerinde çalışma zamanı koşullarına göre değiştirilemez ve etkinlik her örneğinin aynı olacaktır.  
  
## <a name="using-arguments"></a>Bağımsız değişkenleri kullanma  
 Verileri yalnızca bir kez etkinlik yaşam süresi boyunca değerlendirildiğinde bağımsız değişkenleri kullanılmalıdır; diğer bir deyişle, etkinlik yaşam süresi boyunca değerini değiştirmez, ancak değeri farklı örneklerini etkinlik için farklı olabilir. <xref:System.Activities.Statements.If.Condition%2A> bir kez değerlendirilen bir değerin bir örnektir; Bu nedenle, bağımsız değişken olarak tanımlanır. <xref:System.Activities.Statements.WriteLine.Text%2A> başka bir örnek olduğundan yalnızca Etkinlik yürütme sırasında bir kez değerlendirilir, bir bağımsız değişken olarak tanımlanan bir yöntemin olmakla birlikte bu etkinlik için farklı örneklerinde farklı olabilir.  
  
## <a name="using-activityaction"></a>ActivityAction kullanma  
 Birden çok kez ömrünü Etkinlik yürütme sırasında değerlendirilecek verileri gerektiğinde bir <xref:System.Activities.ActivityAction> kullanılmalıdır. Örneğin, <xref:System.Activities.Statements.While.Condition%2A> özelliği, her yineleme için değerlendirilir <xref:System.Activities.Statements.While> döngü. Varsa bir <xref:System.Activities.InArgument> bu amaçla, döngü asla çıkış, bağımsız değişken her yinelemede hesaplanması değil ve her zaman olduğu döndürmesine aynı sonucu kullanıldı.
