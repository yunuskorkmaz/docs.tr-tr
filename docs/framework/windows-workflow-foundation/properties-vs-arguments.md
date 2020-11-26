---
title: Özellikler ve Arguments
ms.date: 03/30/2017
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
ms.openlocfilehash: 2ed443b962e6cccb8a0f670f1dbd744bfa8ed354
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245932"
---
# <a name="properties-vs-arguments"></a>Özellikler ve Arguments

Bir etkinliğe veri geçirmek için kullanabileceğiniz çeşitli seçenekler vardır. Kullanmanın yanı sıra <xref:System.Activities.InArgument> , aynı zamanda standart CLR özellikleri veya ortak özellikler kullanılarak veri alan etkinlikler de geliştirilebilir <xref:System.Activities.ActivityAction> . Bu konu başlığı altında, uygun yöntem türünü seçme açıklanmaktadır.  
  
## <a name="using-clr-properties"></a>CLR özelliklerini kullanma  

 Verileri bir etkinliğe geçirirken, CLR özellikleri (diğer bir deyişle, verileri açığa çıkarmak için Get ve set yordamlarını kullanan ortak Yöntemler) en fazla kısıtlamalara sahip olan seçenektir. CLR özelliğine geçirilen parametrenin değeri, çözüm derlendiğinde bilinmelidir; Bu değer, iş akışının her örneği için aynı olacaktır. Bu şekilde, CLR özelliğine geçirilen bir değer, kodda tanımlanan bir sabit değere benzerdir; Bu değer etkinliğin ömrü için değiştirilemez ve etkinliğin farklı örnekleri için değiştirilemez. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> , bir etkinliğin açığa çıkarılan CLR özelliğine bir örnektir; Etkinlik çağrılarının Yöntem adı çalışma zamanı koşullarına göre değiştirilemez ve etkinliğin her örneği için aynı olacaktır.  
  
## <a name="using-arguments"></a>Bağımsız değişkenleri kullanma  

 Bağımsız değişkenler etkinliğin kullanım ömrü boyunca yalnızca bir kez değerlendirildiğinde kullanılmalıdır; diğer bir deyişle, etkinliğin ömrü boyunca değeri değişmez, ancak değer etkinliğin farklı örnekleri için farklı olabilir. <xref:System.Activities.Statements.If.Condition%2A> bir kez değerlendirilen bir değere örnektir; Bu nedenle, bir bağımsız değişken olarak tanımlanmıştır. <xref:System.Activities.Statements.WriteLine.Text%2A> , etkinliğin yürütülmesi sırasında yalnızca bir kez değerlendirildiğinden ve etkinliğin farklı örnekleri için farklı olabilecek bir bağımsız değişken olarak tanımlanması gereken bir yönteme ait başka bir örnektir.  
  
## <a name="using-activityaction"></a>ActivityAction kullanma  

 Etkinliğin çalışmasının ömrü boyunca verilerin birden çok kez değerlendirilmesi gerektiğinde, <xref:System.Activities.ActivityAction> kullanılması gerekir. Örneğin, <xref:System.Activities.Statements.While.Condition%2A> özellik döngünün her yinelemesi için değerlendirilir <xref:System.Activities.Statements.While> . <xref:System.Activities.InArgument>Bu amaçla kullanıldıysa, bağımsız değişken her yineleme için yeniden değerlendirilmeyeceğinden ve her zaman aynı sonucu döndüren için döngü hiçbir zaman çıkmayacaktır.
