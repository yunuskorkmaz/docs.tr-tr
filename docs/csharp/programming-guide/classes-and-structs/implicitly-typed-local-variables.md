---
title: "Örtülü Olarak Yazılan Yerel Değişkenler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Örtülü Olarak Yazılan Yerel Değişkenler (C# Programlama Kılavuzu)
Yerel değişkenler bir açık tür vermeden bildirilebilir. `var` Anahtar sözcüğü başlatma ifadesinin sağ tarafında ifadesinden değişkeninin türü gerçekleştirip derleyici bildirir. Çıkarılan türü, yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework Sınıf Kitaplığı'nda tanımlanan bir türü olabilir. Dizilerle başlatma hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Aşağıdaki örnekler, yerel değişkenleri bildirilebilir ile çeşitli şekillerde `var`:  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Anlamak önemlidir `var` anahtar sözcüğü "değişken" gelmez ve değişken geniş olduğunu göstermez yazılan veya geç bağlama. Yalnızca derleyici belirler ve en uygun türe atar anlamına gelir.  
  
 `var` Anahtar sözcüğünü aşağıdaki bağlamlarında kullanılır:  
  
-   Yerel değişkenler (yöntemi kapsamda bildirilen değişkenlerin) üzerinde önceki örnekte gösterildiği gibi.  
  
-   İçinde bir [için](../../../csharp/language-reference/keywords/for.md) başlatma deyimi.  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   İçinde bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) başlatma deyimi.  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   İçinde bir [kullanarak](../../../csharp/language-reference/keywords/using-statement.md) deyimi.  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: kullanım örtük olarak yazılan yerel değişkenler ve bir sorgu ifadesinde dizileri](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>var ve anonim türler  
 Çoğunda kullanımını durumlarda `var` isteğe bağlıdır ve yalnızca söz dizimi kolaylık sağlamak. Ancak, bir değişkene sahip anonim bir tür başlatıldığında değişkeni olarak bildirilmelidir `var` sonraki bir zamanda nesnenin özelliklerini erişmeniz gerekiyorsa. Yaygın bir senaryo budur [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri. Daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Kaynak kodunuz perspektifinden anonim bir tür adı yok. Bu nedenle, bir sorgu değişkeni ile başlatılmışsa `var`, döndürülen sırada nesnelerin özelliklerine erişmek için tek yolu kullanmaktır sonra `var` yineleme değişkeni türü olarak `foreach` deyimi.  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Değişken bildirimleri örtük olarak yazılan aşağıdaki kısıtlamalar geçerlidir:  
  
-   `var`yerel bir değişken bildirilen ve aynı deyiminde başlatılmış yalnızca kullanılabilir; Değişken null ya da bir yöntem Grup ya da adsız bir işlev başlatılamaz.  
  
-   `var`sınıf kapsamı alanlarını kullanılamaz.  
  
-   Kullanarak bildirilen değişkenlerin `var` başlatma ifadede kullanılamaz. Bu ifade başka bir deyişle, yasal`: int i = (i = 20);` ancak bu ifade bir derleme zamanı hatası oluşturur:`var i = (i = 20);`  
  
-   Birden çok örtük olarak yazılan değişkenler aynı deyiminde başlatılamaz.  
  
-   Bir tür adlandırırsanız `var` kapsam içinde sonra `var` anahtar sözcüğü bu tür adı çözülür ve bir örtük olarak yazılan yerel değişken bildirimi bir parçası olarak kabul edilmez.  
  
 Bulabilirsiniz `var` sorgu değişkeni tam oluşturulan türünü olduğu belirlemek zor sorgu ifadelerle yararlı olabilir. Bu işlemleri sıralama ve Gruplama ile ortaya çıkabilir.  
  
 `var` Anahtar sözcüğü da yararlı olabilir değişkeni belirli türünü klavyede yazmak sıkıcı veya açık olduğunda veya kod okunabilirliğini eklemez. Bir örneği burada `var` bu yararlıdır şekilde olan Grup işlemleriyle Kullanılanlar gibi iç içe geçmiş genel türler. Aşağıdaki sorguda, sorgu değişkeni türüdür `IEnumerable<IGrouping<string, Student>>`. Sizin ve kodunuzu korumalıdır başkalarının bu anlamak sürece, kolaylık sağlamak ve kısaltma için örtük yazarak kullanarak herhangi bir sorun yoktur.  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Ancak, kullanımını `var` kodunuzu diğer geliştiriciler için anlaşılması daha zor hale getirmek için olası en az yok. Bu nedenle, genellikle C# belgeleri kullanan `var` yalnızca gerekli olduğu zaman.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [Örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [Nasıl yapılır: Kullanım türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri sorgu ifadesinde](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [için](../../../csharp/language-reference/keywords/for.md)  
 [foreach,](../../../csharp/language-reference/keywords/foreach-in.md)  
 [using deyimi](../../../csharp/language-reference/keywords/using-statement.md)
