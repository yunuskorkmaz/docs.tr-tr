---
title: Oluşturucular kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 018710f753df261fce28e2e1cae1272b36923a05
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363011"
---
# <a name="using-constructors-c-programming-guide"></a>Oluşturucular Kullanma (C# Programlama Kılavuzu)

Bir [sınıf](../../../csharp/language-reference/keywords/class.md) veya [Yapı](../../../csharp/language-reference/keywords/struct.md) oluşturulduğunda, Oluşturucusu çağırılır. Oluşturucular, sınıf veya struct ile aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başlatır.  
  
 Aşağıdaki örnekte, adlı `Taxi` bir sınıf basit bir Oluşturucu kullanılarak tanımlanmıştır. Bu sınıf daha sonra [New](../../../csharp/language-reference/operators/new-operator.md) işleciyle oluşturulur. Oluşturucu, yeni nesne için bellek `new` ayrıldıktan hemen sonra operatör tarafından çağrılır. `Taxi`  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 *Parametresiz Oluşturucu*olarak hiçbir parametre alan bir oluşturucuya. Parametresiz oluşturucular, `new` bir nesne işleci kullanılarak oluşturulduğunda ve için `new`bağımsız değişken sağlanamadığında çağrılır. Daha fazla bilgi için bkz. [örnek oluşturucular](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Sınıf [statik](../../../csharp/language-reference/keywords/static.md)olmadığı takdirde, oluşturucuları olmayan sınıflara sınıf örneğini etkinleştirmek için C# derleyici tarafından ortak parametresiz bir Oluşturucu verilirler. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Aşağıdaki gibi, oluşturucuyu özel yaparak bir sınıfın örneğinin oluşturulmasını engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Daha fazla bilgi için bkz. [özel oluşturucular](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 [Yapı](../../../csharp/language-reference/keywords/struct.md) türleri için oluşturucular Sınıf oluşturuculara benzer, ancak `structs` derleyici tarafından otomatik olarak sağlandığı için açık bir parametresiz oluşturucu içeremez. Bu Oluşturucu, `struct` içindeki her bir alanı varsayılan değerlerine başlatır. Daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Ancak, parametresiz Oluşturucu yalnızca ile `struct` `new`örneği belirtilmişse çağrılır. Örneğin, bu kod, için <xref:System.Int32>parametresiz oluşturucuyu kullanır, böylece tamsayı başlatılmış olduğundan emin olmanız gerekir:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Ancak, aşağıdaki kod, bir derleyici hatasına neden olur çünkü kullanmaz `new`ve başlatılmamış bir nesneyi kullanmaya çalışır:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatif olarak, `structs` (tüm yerleşik sayısal türler dahil) tabanlı nesneler başlatılabilir veya atanabilir ve sonra aşağıdaki örnekte olduğu gibi kullanılabilir:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Bu nedenle, bir değer türü için parametresiz oluşturucunun çağrılması gerekli değildir.  
  
 Her iki sınıf `structs` de, parametreleri alan oluşturucular tanımlayabilir. Parametreleri alan oluşturucuların bir `new` ifade veya bir [temel](../../../csharp/language-reference/keywords/base.md) deyimden çağrılması gerekir. Sınıflar ve `structs` Ayrıca birden çok Oluşturucu tanımlayabilir ve parametresiz bir Oluşturucu tanımlamak gerekmez. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Bu sınıf aşağıdaki deyimlerden herhangi biri kullanılarak oluşturulabilir:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Bir Oluşturucu, bir temel `base` sınıfın yapıcısını çağırmak için anahtar sözcüğünü kullanabilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 Bu örnekte, Oluşturucu için blok yürütülmeden önce temel sınıfın Oluşturucusu çağırılır. `base` Anahtar sözcüğü parametresiz ya da olmadan kullanılabilir. Oluşturucuya yönelik parametreler, bir ifadenin parçası olarak veya için `base`parametre olarak kullanılabilir. Daha fazla bilgi için bkz. [Base](../../../csharp/language-reference/keywords/base.md).  
  
 Türetilmiş bir sınıfta, bir temel sınıf Oluşturucu `base` anahtar sözcüğü kullanılarak açıkça çağrılmamasından, varsa parametresiz Oluşturucu örtük olarak çağırılır. Bu, aşağıdaki Oluşturucu bildirimlerinin etkili bir şekilde aynı olduğu anlamına gelir:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Bir temel sınıf parametresiz bir Oluşturucu sunmuyor ise, türetilmiş sınıf kullanarak `base`temel oluşturucuya açık bir çağrı yapmalıdır.  
  
 [Bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğünü kullanarak bir Oluşturucu aynı nesnede başka bir Oluşturucu çağırabilir. Benzer `base`şekilde `this` , parametresiz veya parametresiz olarak kullanılabilir ve kurucudaki tüm parametreler, için `this`parametre olarak veya bir ifadenin parçası olarak kullanılabilir. Örneğin, önceki örnekteki ikinci Oluşturucu kullanılarak `this`yeniden yazılabilir:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Önceki örnekte `this` anahtar sözcüğünün kullanılması, bu oluşturucunun çağrılmasına neden olur:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Oluşturucular [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korunan](../../../csharp/language-reference/keywords/protected.md), [dahili](../../../csharp/language-reference/keywords/internal.md), [korunan iç](../../../csharp/language-reference/keywords/protected-internal.md) veya [özel korumalı](../../../csharp/language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğinize ilişkin tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bir Oluşturucu [static](../../../csharp/language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilemez. Statik oluşturucular, herhangi bir statik alana erişildikten hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmak için kullanılır. Daha fazla bilgi için bkz. [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
