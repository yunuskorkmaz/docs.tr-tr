---
title: Özel akış denetimi etkinlikleri oluşturma
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 124ecd23ca2a856b6efd0e75f816c6f188c9425f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513220"
---
# <a name="creating-custom-flow-control-activities"></a>Özel akış denetimi etkinlikleri oluşturma
.Net Framework benzer şekilde programlama yapıları soyut işlev akış denetimi etkinlikleri çeşitli içerir (gibi <xref:System.Activities.Statements.Flowchart>) veya standart programlama deyimleri (gibi <xref:System.Activities.Statements.If>). Bu konu örnek projelerinden birini mimarisini açıklar [olmayan genel ForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Özel bir sınıf oluşturma  
 Genel olmayan ForEach sınıfın alt etkinlikler zamanlamak ihtiyaç duyacağı beri türetmek gerekir <xref:System.Activities.NativeActivity>, türetilen etkinlikleri itibaren <xref:System.Workflow.Activities.CodeActivity> bu işlevselliğe sahip değil.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 Özel bir sınıf etkinlik tarafından kullanılan verileri depolamak ve etkinliğin alt etkinlikleri yürütmek için işlevselliği sağlamak için birkaç üye gerektirir. Bu üyeleri Ekle:  
  
-   `valueEnumerator`: Genel olmayan <xref:System.Activities.Variable%601> türü <xref:System.Collections.IEnumerator> öğeleri koleksiyon üzerinde döngüyle gezinmek için kullanılır. Bu üye türünde <xref:System.Activities.Variable%601> etkinlik yerine bir bağımsız değişken ya da bu nesnenin etkinlik dışında bir kaynağa sahip gerekiyorsa, kullanılacak ortak özellik dahili olarak kullanıldığından.  
  
-   `OnChildComplete`: Ortak <xref:System.Activities.CompletionCallback> özelliği, her alt yürütme tamamlandığında yürütür. Değeri etkinliğin farklı örnekleri için değiştirmez beri bu üye CLR özelliği olarak tanımlanır.  
  
-   `Values`: Alt etkinlik yineleme için kullanılan girişleri koleksiyonu. Bu üye türünde <xref:System.Activities.InArgument%601>, bu yana veri kaynağını dışında bir etkinliktir ancak koleksiyonunun içeriğini Etkinlik yürütme sırasında değiştirmek için beklenmiyor. Etkinlik (eklemek veya etkinlikleri, örneğin kaldırmak için) etkinlik çalıştırırken bu koleksiyonun içeriğini değiştirme işlevselliği gerekirse, bu üye olarak tanımlanmış bir <xref:System.Activities.ActivityAction>, daha sonra her zaman değerlendirilen Böylece değişiklikleri faaliyete kullanılabilir olur, bunlara.  
  
-   `Body`: Her öğe için yürütülecek etkinliği bu üye tanımlar `Values` koleksiyonu. Bu üye olarak tanımlanan bir <xref:System.Activities.ActivityAction> böylece her erişildiğinde değerlendirilir.  
  
-   `Execute`: Bu yöntem `InternalExecute`, `OnForEachComplete`, ve `GetStateAndExecute` zamanlayarak ve gövde üye tanımlanan alt etkinliğin tamamlanma işleyici atamak için ortak olmayan üyeler.  
  
-   `CacheMetadata`: Bu üye çalışma zamanı etkinliği yürütmek gereken bilgileri sağlar. Varsayılan olarak, bir etkinlik 's `CacheMetadata` yöntemi hakkında bilgilendirmek tüm genel üyeler etkinliğin çalışma zamanı, ancak bu etkinlik için bazı işlevler özel üyelerin kullandığından, onu çalışma zamanı farkında olması için kendi varlığı çalışma zamanı bildirmesi gerekir. bunları. Bu durumda, `CacheMetadata` işlevi geçersiz kılınmıştır böylece özel `valueEnumerator` üye erişilebilir. Bu üye ayrıca değerleri etkinliği için bir bağımsız değişken oluşturur, böylece bunlar etkinliği yürütülürken geçirilebilir.
