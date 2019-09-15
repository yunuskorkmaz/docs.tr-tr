---
title: Özel akış denetimi etkinlikleri oluşturma
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 8e7d4caad197631509fe80a5b5a08eff4d228c1c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989724"
---
# <a name="creating-custom-flow-control-activities"></a>Özel akış denetimi etkinlikleri oluşturma
.NET Framework, soyut programlama yapılarına ( <xref:System.Activities.Statements.Flowchart>gibi) veya standart programlama ifadelerine ( <xref:System.Activities.Statements.If>gibi) benzer şekilde işlev gösteren çeşitli akış denetimi etkinlikleri içerir. Bu konu, [genel olmayan foreach](./samples/non-generic-foreach.md), örnek projelerden birinin mimarisini açıklamaktadır.  
  
## <a name="creating-the-custom-class"></a>Özel sınıf oluşturma  
 Genel olmayan foreach sınıfının alt etkinlikleri zamanlaması gerektiğinden, öğesinden <xref:System.Activities.NativeActivity> <xref:System.Workflow.Activities.CodeActivity> türettikleri etkinlikler bu işlevselliğe sahip olmadığından öğesinden türetilmelidir.  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 Özel sınıf, etkinlik tarafından kullanılan verileri depolamak ve etkinliğin alt etkinliklerini yürütmek için işlevsellik sağlamak üzere çeşitli Üyeler gerektirir. Bu Üyeler şunları içerir:  
  
- `valueEnumerator`: Öğe koleksiyonunu yinelemek için <xref:System.Activities.Variable%601> kullanılan tür <xref:System.Collections.IEnumerator> genel olmayan türü. Bu üye, bu nesnenin <xref:System.Activities.Variable%601> etkinlik dışında bir kaynağı olması durumunda kullanılacak bir bağımsız değişken veya public özelliği değil, etkinlikte dahili olarak kullanıldığı için türündedir.  
  
- `OnChildComplete`: Her alt <xref:System.Activities.CompletionCallback> öğe yürütmeyi tamamladığında yürütülen ortak özellik. Bu üye bir CLR özelliği olarak tanımlanır, çünkü değeri etkinliğin farklı örnekleri için değişmeyecektir.  
  
- `Values`: Alt etkinliğin yinelemeleri için kullanılan girişlerin koleksiyonu. Bu üye, verilerin kaynağı <xref:System.Activities.InArgument%601>etkinliğin dışında olduğundan, ancak koleksiyonun içeriklerinin etkinliğin yürütülmesi sırasında değiştirilmesi beklenmediğinden, bu üye türündedir. Etkinlik yürütülürken bu koleksiyonun içeriğini değiştirme işlevselliğine ihtiyaç duyuldıysa (örneğin, etkinlik eklemek veya kaldırmak için), bu üye bir <xref:System.Activities.ActivityAction>olarak tanımlanmış olur, bu da her seferinde değerlendirilir Bu, değişiklikler etkinlik tarafından kullanılabilir hale gelecek şekilde erişilirdi.  
  
- `Body`: Bu üye `Values` koleksiyondaki her öğe için yürütülecek etkinliği tanımlar. Bu üye, her erişildiği sırada <xref:System.Activities.ActivityAction> değerlendirilmek üzere bir olarak tanımlanır.  
  
- `Execute`: Bu yöntem, yürütmeyi `InternalExecute`zamanlamak `OnForEachComplete`ve gövde üyesinde tanımlanan alt etkinliğin tamamlanma işleyicisini atamak için, ve `GetStateAndExecute` ortak olmayan üyeleri kullanır.  
  
- `CacheMetadata`: Bu üye, çalışma zamanında etkinliği yürütmek için gereken bilgileri sağlar. Varsayılan olarak, bir etkinliğin `CacheMetadata` Yöntemi etkinliğin tüm genel üyelerinin çalışma zamanını bilgilendirir, ancak bu etkinlik bazı işlevler için özel Üyeler kullandığından, çalışma zamanının farkında olması için, çalışma zamanına ait çalışma zamanına bildirmesi gerekir yapıştırabilirsiniz. Bu durumda, `CacheMetadata` özel `valueEnumerator` üyeye erişilebilmesi için işlev geçersiz kılınır. Bu üye, yürütme sırasında etkinliğe geçirilebilmeleri için etkinliğin değerleri için bir bağımsız değişken oluşturur.
