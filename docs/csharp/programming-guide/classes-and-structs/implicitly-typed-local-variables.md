---
title: Örtük olarak yazılan yerel değişkenler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 68c0ff055c91f4f1deca6fcfada0f14577439731
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237018"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Örtülü Olarak Yazılan Yerel Değişkenler (C# Programlama Kılavuzu)
Yerel değişkenler, açık bir tür vermeden bildirilebilir. `var` Başlatma ifadesinin sağ tarafındaki ifade değişkenin türünü çıkarsamak için derleyicinin anahtar sözcüğü bildirir. Çıkarsanan tür, yerleşik bir tür, anonim bir tür, kullanıcı tanımlı bir tür veya .NET Framework Sınıf Kitaplığı'nda tanımlı bir tür olabilir. Dizilerle başlatma hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Aşağıdaki örnekler, yerel değişkenleri bildirilebilir ile çeşitli şekillerde `var`:  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Kavramak önemlidir `var` anahtar sözcüğü, "değişken" anlamına gelmez ve değişken gevşek olduğunu göstermez yazılabilir veya geç bağlama. Yalnızca derleyici belirler ve en uygun türde atar anlamına gelir.  
  
 `var` Anahtar sözcüğü aşağıdaki bağlamlarında kullanılabilir:  
  
-   Yerel değişkenlere (yöntemi kapsamında bildirilen değişkenler) önceki örnekte gösterildiği gibi.  
  
-   İçinde bir [için](../../../csharp/language-reference/keywords/for.md) başlatma ifadesi.  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   İçinde bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) başlatma ifadesi.  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   İçinde bir [kullanarak](../../../csharp/language-reference/keywords/using-statement.md) deyimi.  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Daha fazla bilgi için [nasıl yapılır: Kullanım türü örtük olarak belirlenmiş yerel değişkenleri ve dizileri sorgu ifadesinde](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>var ve anonim türler  
 Çoğu durumda kullanımını `var` isteğe bağlıdır ve yalnızca söz dizimsel kolaylık. Ancak, bir değişken içeren bir anonim tür başlatıldığında olarak değişkeni bildirilmelidir `var` daha sonraki bir noktada nesnenin özelliklerini erişmeniz gerekiyorsa. Bu ortak senaryoda olan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde. Daha fazla bilgi için [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Kaynak kodunuzu açısından bakıldığında, anonim bir tür adı yok. Bu nedenle, bir sorgu değişkeni ile başlatılmışsa `var`, döndürülen dizi nesnelerin özelliklerine erişmek için tek yolu kullanmaktır sonra `var` yineleme değişkeni türü olarak `foreach` deyimi.  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Türü örtük olarak belirlenmiş değişken bildirimleri için aşağıdaki kısıtlamalar uygulanır:  
  
-   `var` yerel bir değişken bildirildi ve aynı deyimde başlatıldı, yalnızca kullanılabilir; değişkeni, null ya da bir yöntem grubu ya da anonim bir işlevdir başlatılamaz.  
  
-   `var` sınıf kapsamı alanları kullanılamaz.  
  
-   Kullanılarak bildirilen değişkenler `var` başlatma ifadesinde kullanılamaz. Diğer bir deyişle, bu ifade yasal`: int i = (i = 20);` ancak bu ifade bir derleme zamanı hatası oluşturur: `var i = (i = 20);`  
  
-   Aynı deyimde birden fazla örtük olarak yazılan değişkenler başlatılamaz.  
  
-   Adlı bir tür ise `var` kapsam içinde olan sonra `var` anahtar sözcüğü bu tür adı için çözümler ve bir örtük olarak belirlenmiş yerel değişken bildirimi bir parçası olarak kabul edilmez.  
  
 İlginizi çekebilecek `var` da yararlı sorgu ifadeleri tam olarak yapılandırılmış sorgu değişkeni türünü olduğu saptamak zor olabilir. Bu gruplandırma ve sıralama işlemleri ile ortaya çıkabilir.  
  
 `var` Anahtar sözcüğü de yararlı olabilir değişkeni türünü yorucu bir süreç klavyede yazın veya açıktır veya kodun okunabilirliğini eklemez. Bir örnek burada `var` bu yararlıdır şekilde olan grubu işlemleri ile Kullanılanlar gibi iç içe geçmiş genel türler. Aşağıdaki sorguda, sorgu değişkeninin türü olduğu `IEnumerable<IGrouping<string, Student>>`. Siz ve kodunuzu korumalıdır başkalarının bunu anlamak sürece örtülü yazma convenience ve kısaltma için kullanma konusunda sorun yoktur.  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Ancak, kullanımını `var` kodunuzu anlamak için diğer geliştiriciler daha zor hale getirmek için olası en az yok. Bu nedenle, genellikle C# belgeleri kullanan `var` yalnızca gerekli olduğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [Örtük Olarak Yazılan Diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
- [Nasıl yapılır: Kullanım yerel değişkenleri ve dizileri sorgu ifadesinde örtük](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
- [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [var](../../../csharp/language-reference/keywords/var.md)  
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [LINQ (dil ile tümleşik sorgu)](../../../csharp/linq/index.md)  
- [for](../../../csharp/language-reference/keywords/for.md)  
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
- [using Deyimi](../../../csharp/language-reference/keywords/using-statement.md)
