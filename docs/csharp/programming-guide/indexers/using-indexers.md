---
title: Dizin oluşturucular kullanma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 4411fe0ffe7dc136b4e74adeba3e5596af3aa1db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589432"
---
# <a name="using-indexers-c-programming-guide"></a>Dizin oluşturucular kullanmaC# (Programlama Kılavuzu)

Dizin oluşturucular, istemci uygulamaların yalnızca bir dizi olarak erişebileceği bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/keywords/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) oluşturmanıza imkan tanıyan sözdizimsel bir kolaydır. Dizin oluşturucular en sık, birincil amacı bir iç koleksiyonu veya diziyi kapsüllemek olan türlerde uygulanır. Örneğin, 24 saatlik bir dönemde 10 farklı `TempRecord` zamanda kaydedildiği gibi Fahrenhayt 'teki sıcaklığı temsil eden bir sınıfınız olduğunu varsayalım. Sınıfı, sıcaklık değerlerini depolamak `temps` için türünde `float[]` bir dizi içerir. Bu sınıfta bir Dizin Oluşturucu uygulayarak istemciler, gibi bir `TempRecord` `float temp = tr[4]` örnekteki sıcakya farklı `float temp = tr.temps[4]`şekilde erişebilir. Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için söz dizimini basitleştirir; Ayrıca, diğer geliştiricilerin anlayabilmesi için sınıfı ve amacını daha sezgisel hale getirir.  
  
Bir sınıf veya yapı biriminde bir Dizin Oluşturucu bildirmek için aşağıdaki örnekte gösterildiği gibi [this](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanın:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Açıklamalar

Bir dizin oluşturucunun türü ve parametrelerinin türü en az dizin oluşturucunun kendisi olarak erişilebilir olmalıdır. Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../language-reference/keywords/access-modifiers.md).  
  
 Arabirim ile Dizin oluşturucular kullanma hakkında daha fazla bilgi için bkz. [arabirim dizin oluşturucular](./indexers-in-interfaces.md).  
  
 Bir dizin oluşturucunun imzası, biçimsel parametrelerinin sayısı ve türlerinden oluşur. Dizin Oluşturucu türü veya biçimsel parametrelerin adlarını içermez. Aynı sınıfta birden fazla Dizin Oluşturucu bildirirseniz, bunların farklı imzaları olmalıdır.  
  
 Dizin Oluşturucu değeri bir değişken olarak sınıflandırılmıyor; Bu nedenle, Dizin Oluşturucu değeri bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçirilemez.  
  
 Dizin oluşturucuyu diğer dillerin kullanabileceği bir adla sağlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>kullanın:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Bu dizin oluşturucunun adı `TheItem`olacaktır. Ad özniteliği sağlanmaması varsayılan adı yapar `Item` .  
  
## <a name="example-1"></a>Örnek 1  
  
Aşağıdaki örnek, bir özel dizi alanının, `temps`ve bir dizin oluşturucunun nasıl bildirilemeyeceğini gösterir. Dizin Oluşturucu örneğe `tempRecord[i]`doğrudan erişim sağlar. Dizin oluşturucuyu kullanmanın alternatifi, diziyi [ortak](../../language-reference/keywords/public.md) bir üye olarak bildirmeli ve üyelerine `tempRecord.temps[i]`doğrudan erişim sağlar.  
  
 Bir dizin oluşturucunun erişim değerlendirildiği zaman, örneğin bir `Console.Write` ifadede, [Get](../../language-reference/keywords/get.md) erişimcisinin çağrıldığına dikkat edin. Bu nedenle, `get` bir erişimci yoksa, bir derleme zamanı hatası oluşur.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Diğer değerleri kullanarak dizin oluşturma

C#Dizin Oluşturucu parametre türü tamsayı olarak sınırlandırmaz. Örneğin, bir Dizin Oluşturucu ile dize kullanmak yararlı olabilir. Bu tür bir Dizin Oluşturucu koleksiyondaki dizeyi arayarak ve uygun değeri döndürerek uygulanabilir. Erişimciler aşırı yüklenmiş olabilir, dize ve tamsayı sürümleri birlikte bulunabilir.  
  
## <a name="example-2"></a>Örnek 2  
  
Aşağıdaki örnek, haftanın günlerini depolayan bir sınıf bildirir. `get` Erişimci bir dize, bir günün adı alır ve karşılık gelen tamsayıyı döndürür. Örneğin, "Pazar" 0, "Pazartesi" 1 döndürür ve bu şekilde devam eder.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Güçlü programlama

 Dizin oluşturucularının güvenliğinin ve güvenilirliğinin iyileşmesi için kullanabileceğiniz iki ana yol vardır:  
  
- İstemci kodunun geçersiz bir dizin değeri geçirme olasılığını işlemek için bir tür hata işleme stratejisi eklediğinizden emin olun. Bu konunun önceki kısımlarında yer alan ilk örnekte, TempRecord sınıfı, istemci kodun dizin oluşturucuya geçirmeden önce girişi doğrulamasını sağlayan bir length özelliği sağlar. Hata işleme kodunu dizin oluşturucunun içine de yerleştirebilirsiniz. Bir Dizin Oluşturucu erişimcisinde oluşturduğunuz tüm özel durumları kullanıcılara belgelediğinizden emin olun.  
  
- [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcilerinin erişilebilirliğini makul olacak şekilde kısıtlayıcı olarak belirleyin. Bu, `set` özellikle erişimcinin açısından önemlidir. Daha fazla bilgi için bkz. [erişimci erişilebilirliğini kısıtlama](../classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
