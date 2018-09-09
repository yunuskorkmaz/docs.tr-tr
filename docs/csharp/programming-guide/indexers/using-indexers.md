---
title: Dizin Oluşturucular Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 3e4c1f346b83cf97c57a359984bd08e075b6451b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253227"
---
# <a name="using-indexers-c-programming-guide"></a>Dizin Oluşturucular Kullanma (C# Programlama Kılavuzu)
Dizin oluşturucular özelliklere oluşturmanıza olanak sağlayan bir söz dizimi kullanışlı bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [yapı](../../../csharp/language-reference/keywords/struct.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md) istemci uygulamaları bir dizi olarak erişebilirsiniz. Dizin Oluşturucular, bir iç toplama veya dizi yalıtılacak birincil amacı olan türlerinde en sık uygulanır. Örneğin, 24 saatlik dönemde 10 farklı zamanlarda kayıtlı Farenheit sıcaklık temsil eden TempRecord adlı bir sınıf olduğunu varsayalım. "Sıcaklıkların temsil etmek için koşulları" tür float adlı bir dizi sınıf içerir ve bir <xref:System.DateTime> Sıcaklıkların kaydedilme tarihi temsil eder. Bu sınıfta dizin oluşturucu uygulayarak, istemciler de TempRecord örnek olarak sıcaklıklar erişebilir `float temp = tr[4]` yerine olarak `float temp = tr.temps[4]`. Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için sözdizimini basitleştirir; Ayrıca sınıfı ve amacını anlamak diğer geliştiriciler için daha kolay kılar.  
  
 Bir dizin oluşturucu, bir sınıf veya yapı bildirmek için kullanın [bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü, bu örnekte olduğu gibi:  
  
```  
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
  
 Dizin oluşturucunun diğer dillerin kullanabileceği bir ad ile sağlayacak bir `name` bildiriminde özniteliği. Örneğin:  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Bu dizin oluşturucu adı gerekir `TheItem`. Ad özniteliği bulunmaması olun `Item` varsayılan adı.  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir dizi özel alanı bildirmek gösterilmektedir `temps`ve dizin oluşturucu. Dizin oluşturucu örneği doğrudan erişim sağlayan `tempRecord[i]`. Dizin Oluşturucusu kullanmaya alternatif olarak bir diziyi bildirmek için olan bir [genel](../../../csharp/language-reference/keywords/public.md) üyesi ve üyeleri, erişim `tempRecord.temps[i]`, doğrudan.  
  
 Bir oluşturucunun erişim, örneğin, içinde çalışırken dikkat bir `Console.Write` deyimi [alma](../../../csharp/language-reference/keywords/get.md) erişimci çağrılır. Bu nedenle, hiçbir `get` erişimci yoksa, bir derleme zamanı hatası oluşur.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Diğer değerleri kullanarak dizin oluşturma  
 C# dizin türü tamsayı kısıtlamaz. Örneğin, bir dizeyi bir dizin oluşturucu ile kullanmak yararlı olabilir. Böyle bir dizin oluşturucu, koleksiyondaki dize için arama ve uygun değeri döndüren uygulanabilir. Dize ve tamsayı sürümleri, erişimcileri aşırı yüklenebilir olarak birlikte bulunabilir.  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Bu örnekte, bir sınıf, Haftanın günlerinin ingilizceleridir depolayan bildirilir. A `get` erişimci bildirilen bir dize, bir günün adını alır ve karşılık gelen bir tamsayı döndürür. Örneğin, Pazar 0 değerini döndürür, Pazartesi 1 döndürür ve benzeri.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 İçinde güvenlik ve dizin oluşturucular güvenilirliğini geliştirilebilir başlıca iki yolu vardır:  
  
-   Herhangi bir türde istemci kodu içinde geçersiz dizin değeri geçirme olasılığını işlemek için hata işleme stratejisi birleştirmek emin olun. Bu konunun önceki kısımlarında ilk örnekte TempRecord sınıf girişi için dizin oluşturucuyu iletmeden önce doğrulamak istemci kodu sağlayan bir uzunluk özelliği sağlar. Hata işleme kod içinde dizin oluşturucunun kendisi de koyabilirsiniz. Kullanıcılar için belge içinde bir dizin oluşturucu erişimci throw özel durumları emin olun.  
  
-   Erişilebilirliğini ayarlamak `get` ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) şüphelenilebilir olabildiğince kısıtlayıcı erişimcileri. Bu önemlidir `set` özellikle erişimcisi. Daha fazla bilgi için [erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
