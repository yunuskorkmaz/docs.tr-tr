---
title: Özel akış denetimi etkinlikleri oluşturma
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 92d98d33b10e431248c4c482fcd26f3036c4c330
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242077"
---
# <a name="creating-custom-flow-control-activities"></a>Özel akış denetimi etkinlikleri oluşturma

.NET Framework, soyut programlama yapılarına (gibi <xref:System.Activities.Statements.Flowchart> ) veya standart programlama ifadelerine (gibi) benzer şekilde işlev gösteren çeşitli akış denetimi etkinlikleri içerir <xref:System.Activities.Statements.If> . Bu konu, [genel olmayan foreach](./samples/non-generic-foreach.md), örnek projelerden birinin mimarisini açıklamaktadır.  
  
## <a name="creating-the-custom-class"></a>Özel sınıf oluşturma  

 Genel olmayan ForEach sınıfının alt etkinlikleri zamanlaması gerektiğinden, öğesinden türettikleri <xref:System.Activities.NativeActivity> Etkinlikler <xref:System.Workflow.Activities.CodeActivity> Bu işlevselliğe sahip olmadığından öğesinden türetilmelidir.  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 Özel sınıf, etkinlik tarafından kullanılan verileri depolamak ve etkinliğin alt etkinliklerini yürütmek için işlevsellik sağlamak üzere çeşitli Üyeler gerektirir. Bu Üyeler şunları içerir:  
  
- `valueEnumerator`: <xref:System.Activities.Variable%601> <xref:System.Collections.IEnumerator> Öğe koleksiyonunu yinelemek için kullanılan tür genel olmayan türü. Bu üye, <xref:System.Activities.Variable%601> Bu nesnenin etkinlik dışında bir kaynağı olması durumunda kullanılacak bir bağımsız değişken veya public özelliği değil, etkinlikte dahili olarak kullanıldığı için türündedir.  
  
- `OnChildComplete`: <xref:System.Activities.CompletionCallback> Her alt öğe yürütmeyi tamamladığında yürütülen ortak özellik. Bu üye bir CLR özelliği olarak tanımlanır, çünkü değeri etkinliğin farklı örnekleri için değişmeyecektir.  
  
- `Values`: Alt etkinliğin yinelemeleri için kullanılan giriş koleksiyonu. Bu üye <xref:System.Activities.InArgument%601> , verilerin kaynağı etkinliğin dışında olduğundan, ancak koleksiyonun içeriklerinin etkinliğin yürütülmesi sırasında değiştirilmesi beklenmediğinden, bu üye türündedir. Etkinlik, etkinlik yürütülürken bu koleksiyonun içeriğini değiştirmek için gereken işlevselliği içeriyorsa (örneğin, etkinlik eklemek veya kaldırmak için), bu üye bir olarak tanımlanır <xref:System.Activities.ActivityAction> ve bu nedenle, değişiklikler etkinlik tarafından kullanılabilir hale gelir.  
  
- `Body`: Bu üye koleksiyondaki her öğe için yürütülecek etkinliği tanımlar `Values` . Bu üye <xref:System.Activities.ActivityAction> , her erişildiği sırada değerlendirilmek üzere bir olarak tanımlanır.  
  
- `Execute`: Bu yöntem, `InternalExecute` `OnForEachComplete` `GetStateAndExecute` yürütmeyi zamanlamak ve gövde üyesinde tanımlanan alt etkinliğin tamamlanma işleyicisini atamak için, ve ortak olmayan üyeleri kullanır.  
  
- `CacheMetadata`: Bu üye, etkinliği yürütmek için gereken bilgileri çalışma zamanına sağlar. Varsayılan olarak, etkinliğin `CacheMetadata` Yöntemi etkinliğin tüm genel üyelerinin çalışma zamanını bilgilendirir, ancak bu etkinlik bazı işlevler için özel Üyeler kullandığından, çalışma zamanının, çalışma zamanının farkında olması için kendi çalışma zamanına bildirmesi gerekir. Bu durumda, `CacheMetadata` özel üyeye erişilebilmesi için işlev geçersiz kılınır `valueEnumerator` . Bu üye, yürütme sırasında etkinliğe geçirilebilmeleri için etkinliğin değerleri için bir bağımsız değişken oluşturur.
