---
title: Özel akış denetimi etkinlikleri oluşturma
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: f457e6f8cefd7183ca20cb449adf1ac15d7bde79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647144"
---
# <a name="creating-custom-flow-control-activities"></a>Özel akış denetimi etkinlikleri oluşturma
.NET Framework programlama yapıları soyutlamak için benzer şekilde işlev akış denetimi etkinlikleri çeşitli içerir (gibi <xref:System.Activities.Statements.Flowchart>) veya standart programlama deyimlerinin (gibi <xref:System.Activities.Statements.If>). Bu konu örnek projelerinden birini mimarisini açıklar [genel olmayan ForEach](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Özel bir sınıf oluşturma  
 Alt etkinlikler zamanlamak genel olmayan ForEach sınıfı gerektirdiğinden türetmek gerekli <xref:System.Activities.NativeActivity>, türetilen etkinlikleri beri <xref:System.Workflow.Activities.CodeActivity> bu işlevselliğe sahip değiliz.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 Özel bir sınıf, etkinlik tarafından kullanılan verileri depolamak ve etkinliğin alt etkinlikleri yürütmek için işlevselliği sağlamak için birçok üye gerektirir. Bu üyeleri Ekle:  
  
- `valueEnumerator`: Genel olmayan <xref:System.Activities.Variable%601> türü <xref:System.Collections.IEnumerator> öğelerinin koleksiyon üzerinde yinelemek için kullanılır. Bu üye türünde <xref:System.Activities.Variable%601> etkinlik yerine bir bağımsız değişken ya da bu nesne bir etkinlik dışında bir kaynağa sahip gerekiyorsa, kullanılacak ortak özelliği, dahili olarak kullanıldığından.  
  
- `OnChildComplete`: Genel <xref:System.Activities.CompletionCallback> özelliği, her alt yürütme tamamlandığında yürütür. Etkinlik için farklı örnekleri değerini değiştirmez olduğundan bu üye bir CLR özelliği olarak tanımlanır.  
  
- `Values`: Alt etkinlik yinelemeleri için kullanılan girişleri koleksiyonu. Bu üye türünde <xref:System.Activities.InArgument%601>, olduğundan veri kaynağı dışında bir etkinlik olduğu halde koleksiyonun içeriğini etkinliği yürütülmesi sırasında değiştirmek için beklenmiyor. Etkinliğin etkinlik (eklemek veya etkinlikleri, örneğin kaldırmak için) çağırılma yürütüldüğü sırada bu koleksiyonun içeriğini değiştirmek için işlevselliği gerekirse, bu üye olarak tanımlanmış bir <xref:System.Activities.ActivityAction>, daha sonra her zaman değerlendirilen değişiklikler etkinlik için kullanılabilir hale gelir, bu, erişildi.  
  
- `Body`: Bu üye her öğe için çalıştırılacak etkinlik tanımlar `Values` koleksiyonu. Bu üye olarak tanımlanan bir <xref:System.Activities.ActivityAction> böylece her erişildiğinde değerlendirilir.  
  
- `Execute`: Bu yöntemde `InternalExecute`, `OnForEachComplete`, ve `GetStateAndExecute` zamanlayarak ve gövde üye tanımlanan alt etkinliğin tamamlama işleyicisine atamak için genel olmayan üyeleri.  
  
- `CacheMetadata`: Bu üye, çalışma zamanı etkinliğini yürütmek gerekli bilgileri sağlar. Varsayılan olarak, bir etkinlik 's `CacheMetadata` yöntemi hakkında bilgilendirmek tüm genel üyeleri etkinliğin çalışma zamanı, ancak bu etkinlik için bazı işlevler özel üyeler kullandığından, bu çalışma zamanı farkında olabilir, böylece kendi varlığı çalışma zamanını bildirmesi gerekir. bunları. Bu durumda, `CacheMetadata` işlevi geçersiz kılınmıştır. böylece özel `valueEnumerator` üye erişilebilir. Böylece bunlar etkinliği yürütülürken geçirilebilir bu üye bir bağımsız değişken değerleri etkinlik için de oluşturur.
