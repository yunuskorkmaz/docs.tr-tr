---
title: Oluşturucular kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: cb6a0befb9e2e628f066061282532513019c1419
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418732"
---
# <a name="using-constructors-c-programming-guide"></a>Oluşturucular Kullanma (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) oluşturulduğunda, Oluşturucusu çağırılır. Oluşturucular, sınıf veya struct ile aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başlatır.  
  
 Aşağıdaki örnekte, `Taxi` adlı bir sınıf basit bir Oluşturucu kullanılarak tanımlanır. Bu sınıf daha sonra [New](../../language-reference/operators/new-operator.md) işleciyle oluşturulur. `Taxi` Oluşturucusu, yeni nesne için bellek ayrıldıktan hemen sonra `new` işleci tarafından çağrılır.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 *Parametresiz Oluşturucu*olarak hiçbir parametre alan bir oluşturucuya. Parametresiz oluşturucular, bir nesne `new` işleci kullanılarak örneklendiğinde ve `new`için herhangi bir bağımsız değişken sağlanmadıkça çağrılır. Daha fazla bilgi için bkz. [örnek oluşturucular](./instance-constructors.md).  
  
 Sınıf [statik](../../language-reference/keywords/static.md)olmadığı takdirde, oluşturucuları olmayan sınıflara sınıf örneğini etkinleştirmek için C# derleyici tarafından ortak parametresiz bir Oluşturucu verilirler. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).  
  
 Aşağıdaki gibi, oluşturucuyu özel yaparak bir sınıfın örneğinin oluşturulmasını engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Daha fazla bilgi için bkz. [özel oluşturucular](./private-constructors.md).  
  
 [Yapı](../../language-reference/keywords/struct.md) türleri için oluşturucular Sınıf oluşturuculara benzer, ancak `structs` derleyici tarafından otomatik olarak sağlandığı için açık parametresiz bir oluşturucu içeremez. Bu Oluşturucu `struct` her alanı varsayılan değerlerine başlatır. Daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md). Ancak, bu parametresiz Oluşturucu yalnızca `struct` `new`ile birlikte oluşturulduğunda çağrılır. Örneğin, bu kod, tamsayının başlatıldığından emin olmak için <xref:System.Int32>parametresiz oluşturucuyu kullanır.  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Ancak, aşağıdaki kod, bir derleyici hatasına neden olur çünkü `new`kullanmaz ve başlatılmamış bir nesneyi kullanmaya çalışır:  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatif olarak, `structs` tabanlı nesneler (tüm yerleşik sayısal türler dahil) başlatılabilir veya atanabilir ve daha sonra aşağıdaki örnekte olduğu gibi kullanılabilir:  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Bu nedenle, bir değer türü için parametresiz oluşturucunun çağrılması gerekli değildir.  
  
 Her iki sınıf ve `structs` de parametre alma oluşturucuları tanımlayabilir. Parametreleri alan oluşturucuların bir `new` ifadesiyle veya bir [taban](../../language-reference/keywords/base.md) ifadesiyle çağrılması gerekir. Sınıflar ve `structs` de birden çok Oluşturucu tanımlayabilir ve parametresiz bir Oluşturucu tanımlamak gerekmez. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Bu sınıf aşağıdaki deyimlerden herhangi biri kullanılarak oluşturulabilir:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Bir Oluşturucu, bir temel sınıfın yapıcısını çağırmak için `base` anahtar sözcüğünü kullanabilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 Bu örnekte, Oluşturucu için blok yürütülmeden önce temel sınıfın Oluşturucusu çağırılır. `base` anahtar sözcüğü parametresiz ya da olmadan kullanılabilir. Oluşturucuya yönelik tüm parametreler `base`parametre olarak veya bir ifadenin bir parçası olarak kullanılabilir. Daha fazla bilgi için bkz. [Base](../../language-reference/keywords/base.md).  
  
 Türetilmiş bir sınıfta, bir temel sınıf oluşturucu açıkça `base` anahtar sözcüğü kullanılarak çağrılmamasından, varsa parametresiz Oluşturucu örtük olarak çağırılır. Bu, aşağıdaki Oluşturucu bildirimlerinin etkili bir şekilde aynı olduğu anlamına gelir:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Bir temel sınıf parametresiz bir Oluşturucu sunmuyor ise, türetilmiş sınıf `base`kullanarak temel oluşturucuya açık bir çağrı vermelidir.  
  
 [Bu](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanarak bir Oluşturucu aynı nesnede başka bir Oluşturucu çağırabilir. `base`gibi, `this` parametresiz veya parametresiz olarak kullanılabilir ve kurucudaki herhangi bir parametre `this`parametre olarak veya bir ifadenin parçası olarak kullanılabilir. Örneğin, önceki örnekteki ikinci Oluşturucu `this`kullanılarak yeniden yazılabilir:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Önceki örnekte `this` anahtar sözcüğünün kullanılması, bu oluşturucunun çağrılmasına neden olur:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Oluşturucular [ortak](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korunan](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğinize ilişkin tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
 Bir Oluşturucu [static](../../language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilemez. Statik oluşturucular, herhangi bir statik alana erişildikten hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmak için kullanılır. Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
