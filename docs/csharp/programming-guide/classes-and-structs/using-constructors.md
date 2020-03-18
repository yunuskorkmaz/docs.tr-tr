---
title: Constructors kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626418"
---
# <a name="using-constructors-c-programming-guide"></a>Oluşturucular Kullanma (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/builtin-types/struct.md) oluşturulduğunda, oluşturucusu çağrılır. Oluşturucular sınıf veya yapıyla aynı ada sahiptir ve genellikle yeni nesnenin veri üyelerini başharfe adaverirler.  
  
 Aşağıdaki örnekte, adlı `Taxi` bir sınıf basit bir oluşturucu kullanılarak tanımlanır. Bu sınıf daha sonra [yeni](../../language-reference/operators/new-operator.md) işleç ile anında. Kurucu, `Taxi` bellek yeni nesne `new` için ayrıldıktan hemen sonra işleç tarafından çağrılır.  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 Parametresiz yapıcı olarak adlandırılan bir oluşturucuya *parametresiz yapıcı*denir. Parametresiz yapıcılar, bir nesne `new` işleç kullanılarak anında anında çağrıldığınızda ve `new`hiçbir bağımsız değişken sağlanmadığında. Daha fazla bilgi için [Bkz. Örnek Oluşturucular.](./instance-constructors.md)  
  
 Sınıf [statik](../../language-reference/keywords/static.md)olmadığı sürece, oluşturucuolmayan sınıflara c# derleyicisi tarafından sınıf anlık oluşturmayı etkinleştirmek için ortak parametresiz bir yapıyapıcı verilir. Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](./static-classes-and-static-class-members.md)bakın.  
  
 Aşağıdaki gibi, oluşturucu özel yaparak bir sınıfın anlık olmasını önleyebilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Daha fazla bilgi için Bkz. [Özel Yapıcılar.](./private-constructors.md)  
  
 [Yapı](../../language-reference/builtin-types/struct.md) türleri için oluşturucular sınıf oluşturucularına `structs` benzer, ancak derleyici tarafından otomatik olarak sağlandığı için açık bir parametresiz oluşturucu içeremez. Bu oluşturucu varsayılan `struct` [değerdeki](../../language-reference/builtin-types/default-values.md)her alanı başharfe döndürdü. Ancak, bu parametresiz oluşturucu yalnızca `struct` `new`. Örneğin, bu kod parametresiz oluşturucuyu <xref:System.Int32>kullanır, böylece tamsayının baş harfe harfle başharfe atılacağından emin olabilirsiniz:  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Ancak, aşağıdaki kod, kullanmadığı `new`ve baş harflere başledilmemiş bir nesneyi kullanmaya çalıştığından derleyici hatasına neden olur:  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatif olarak, (tüm `structs` yerleşik sayısal türler dahil) temel alan nesneler baş harflerle başharflere alınabilir veya atanabilir ve aşağıdaki örnekte olduğu gibi kullanılabilir:  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Bu nedenle, parametresiz oluşturucuyu bir değer türü için çağırmak gerekli değildir.  
  
 Her iki `structs` sınıf ve parametreleri alan yapıcılar tanımlayabilirsiniz. Parametreleri alan yapıcılar bir `new` deyim veya [temel](../../language-reference/keywords/base.md) deyim aracılığıyla çağrılmalıdır. Sınıflar `structs` ve aynı zamanda birden çok oluşturucu tanımlayabilirsiniz ve ne parametresiz bir oluşturucu tanımlamak için gerekli değildir. Örnek:  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 Bu sınıf aşağıdaki ifadelerden biri kullanılarak oluşturulabilir:  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 Bir oluşturucu, `base` bir taban sınıfın oluşturucusu aramak için anahtar sözcüğü kullanabilirsiniz. Örnek:  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 Bu örnekte, taban sınıf için oluşturucu, oluşturucu için blok yürütülmeden önce çağrılır. Anahtar `base` kelime parametreleri ile veya olmadan kullanılabilir. Oluşturucuya ait parametreler, bir `base`ifadenin parametreleri olarak veya bir ifadenin parçası olarak kullanılabilir. Daha fazla bilgi için [temele](../../language-reference/keywords/base.md)bakın.  
  
 Türemiş bir sınıfta, bir taban sınıf oluşturucu `base` anahtar sözcüğü kullanılarak açıkça çağrılmazsa, parametresiz oluşturucu, varsa, örtülü olarak çağrılır. Bu, aşağıdaki oluşturucu bildirimlerin etkili bir şekilde aynı olduğu anlamına gelir:  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 Taban sınıf parametresiz bir oluşturucu sunmuyorsa, türetilmiş sınıfın kullanarak bir `base`temel oluşturucuya açık bir çağrı yapması gerekir.  
  
 Bir oluşturucu [bu](../../language-reference/keywords/this.md) anahtar sözcüğü kullanarak aynı nesnedeki başka bir oluşturucuyu çağırabilir. Gibi `base` `this` , parametreleri ile veya olmadan kullanılabilir ve oluşturucu herhangi `this`bir parametre parametreleri olarak kullanılabilir , ya da bir ifadenin bir parçası olarak. Örneğin, önceki örnekteki ikinci oluşturucu aşağıdakiler `this`kullanılarak yeniden yazılabilir:  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 Önceki örnekte `this` anahtar kelimenin kullanımı bu oluşturucunun çağrılmasını neden olur:  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 Yapıcılar [kamu,](../../language-reference/keywords/public.md) [özel,](../../language-reference/keywords/private.md) [korumalı,](../../language-reference/keywords/protected.md) [dahili,](../../language-reference/keywords/internal.md) [korumalı iç](../../language-reference/keywords/protected-internal.md) veya özel [korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiriciler, sınıfın kullanıcılarının sınıfı nasıl oluşturabileceğini tanımlar. Daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.  
  
 Bir oluşturucu [statik](../../language-reference/keywords/static.md) anahtar sözcüğü kullanılarak statik olarak bildirilebilir. Statik oluşturucular, statik alanlara erişilmeden hemen önce otomatik olarak çağrılır ve genellikle statik sınıf üyelerini başlatmaya kullanılır. Daha fazla bilgi için Statik [Oluşturucular'a](./static-constructors.md)bakın.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Örnek oluşturucular](~/_csharplang/spec/classes.md#instance-constructors) ve [Statik oluşturucular'a](~/_csharplang/spec/classes.md#static-constructors) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
