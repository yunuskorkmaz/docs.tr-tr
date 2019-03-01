---
title: Dizin oluşturucular - kullanarak C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: b74e4375464cc515a281922cb1d5b5b0d1dd1954
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969415"
---
# <a name="using-indexers-c-programming-guide"></a>Dizin oluşturucular (C# programlama Kılavuzu) kullanma

Dizin oluşturucular özelliklere oluşturmanıza olanak sağlayan bir söz dizimi kullanışlı bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapı](../../../csharp/language-reference/keywords/struct.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md) istemci uygulamaları bir dizi olarak erişebilirsiniz. Dizin Oluşturucular, bir iç toplama veya dizi yalıtılacak birincil amacı olan türlerinde en sık uygulanır. Örneğin, bir sınıf olduğunu varsayalım `TempRecord` temsil eden Farenheit sıcaklık bir 24 saatlik dönemde 10 farklı zamanlarda kayıtlı. Sınıfı bir dizi içeren `temps` türü `float[]` sıcaklık değerleri depolamak için. Bu sınıfta dizin oluşturucu uygulayarak istemcileri olarak sıcaklıklar erişebilir bir `TempRecord` örneği `float temp = tr[4]` yerine olarak `float temp = tr.temps[4]`. Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için sözdizimini basitleştirir; Ayrıca sınıfı ve amacını anlamak diğer geliştiriciler için daha kolay kılar.  
  
Bir dizin oluşturucu, bir sınıf veya yapı bildirmek için kullanın [bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Açıklamalar

Bir dizin oluşturucu türüne ve parametrelerinin türü, en az Indexer olarak erişilebilir olması gerekir. Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Dizin oluşturucular bir arabirim ile kullanma hakkında daha fazla bilgi için bkz. [arabirim dizin oluşturucuları](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 Bir dizin oluşturucu imzası, sayı ve biçimsel parametrelerinin türleri oluşur. Dizin Oluşturucu türü veya biçimsel parametrelerinin adları içermez. Aynı sınıf içinde birden fazla dizin oluşturucu bildirirseniz, bunlar farklı imzalarına sahip olmalıdır.  
  
 Bir dizin oluşturucu değeri bir değişkene sınıflandırılmaz; Bu nedenle, bir dizin oluşturucu değer olarak geçirilemez bir [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi.  
  
 Dizin oluşturucunun diğer dillerin kullanabileceği bir ad ile sağlamak için kullanın <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>aşağıdaki örnekte gösterildiği gibi:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Bu dizin oluşturucu adı gerekir `TheItem`. Ad özniteliği bulunmaması olun `Item` varsayılan adı.  
  
## <a name="example-1"></a>Örnek 1  
  
Aşağıdaki örnek, bir dizi özel alanı bildirmek gösterilmektedir `temps`ve dizin oluşturucu. Dizin oluşturucu örneği doğrudan erişim sağlayan `tempRecord[i]`. Dizin Oluşturucusu kullanmaya alternatif olarak bir diziyi bildirmek için olan bir [genel](../../../csharp/language-reference/keywords/public.md) üyesi ve üyeleri, erişim `tempRecord.temps[i]`, doğrudan.  
  
 Bir oluşturucunun erişim, örneğin, içinde çalışırken dikkat bir `Console.Write` deyimi [alma](../../../csharp/language-reference/keywords/get.md) erişimci çağrılır. Bu nedenle, hiçbir `get` erişimci yoksa, bir derleme zamanı hatası oluşur.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Diğer değerleri kullanarak dizin oluşturma

C#Dizin Oluşturucu parametre türü tamsayı kısıtlamaz. Örneğin, bir dizeyi bir dizin oluşturucu ile kullanmak yararlı olabilir. Böyle bir dizin oluşturucu, koleksiyondaki dize için arama ve uygun değeri döndüren uygulanabilir. Dize ve tamsayı sürümleri, erişimcileri aşırı yüklenebilir olarak birlikte bulunabilir.  
  
## <a name="example-2"></a>Örnek 2  
  
Aşağıdaki örnek, Haftanın günlerinin ingilizceleridir depolayan bir sınıfı bildirir. A `get` erişimci bir dize, bir günün adını alır ve karşılık gelen bir tamsayı döndürür. Örneğin, "Sunday" 0 değerini döndürür, 1 ve benzeri "Pazartesi" döndürür.  
  
[!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Güçlü programlama

 İçinde güvenlik ve dizin oluşturucular güvenilirliğini geliştirilebilir başlıca iki yolu vardır:  
  
- Herhangi bir türde istemci kodu içinde geçersiz dizin değeri geçirme olasılığını işlemek için hata işleme stratejisi birleştirmek emin olun. Bu konunun önceki kısımlarında ilk örnekte TempRecord sınıf girişi için dizin oluşturucuyu iletmeden önce doğrulamak istemci kodu sağlayan bir uzunluk özelliği sağlar. Hata işleme kod içinde dizin oluşturucunun kendisi de koyabilirsiniz. Kullanıcılar için belge içinde bir dizin oluşturucu erişimci throw özel durumları emin olun.  
  
- Erişilebilirliğini ayarlamak [alma](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) şüphelenilebilir olabildiğince kısıtlayıcı erişimcileri. Bu önemlidir `set` özellikle erişimcisi. Daha fazla bilgi için [erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
