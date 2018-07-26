---
title: new İşleci (C# Başvurusu)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243953"
---
# <a name="new-operator-c-reference"></a>new İşleci (C# Başvurusu)
Nesneleri oluşturmak ve oluşturucuları çağırmak için kullanılır. Örneğin:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 Ayrıca, anonim türlerin örneklerini oluşturmak için kullanılır:  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` İşleci değer türleri için varsayılan oluşturucuyu çağırmak için de kullanılır. Örneğin:  
  
```csharp
int i = new int();  
```  
  
 Önceki deyim içinde `i` değerine ayarlanır `0`, türü için varsayılan değer olan `int`. Deyimi aşağıdaki aynı etkiye sahiptir:  
  
```csharp
int i = 0;  
```  
  
 Varsayılan değerlerin tam listesi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 İçin varsayılan oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapı](../../../csharp/language-reference/keywords/struct.md) her değer türü örtük olarak bir genel varsayılan oluşturucuya sahip olduğundan. Parametreli oluşturucular ilk değerleri ayarlamak için bir yapı türü bildirmek mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekiyorsa gereklidir.  
  
 Hem yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak edilir, ancak içeren bağlamları kaldırıldığında, bu başvuru türü nesneler çöp tarafından yok ise değer türü nesneler yok edilir Toplayıcı bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen bir zaman. Dosya tanıtıcıları veya ağ bağlantıları gibi kaynakları içeren türleri için içerdikleri kaynakları hemen serbest emin olmak için belirleyici temizleme kullanmayı tercih edilir. Daha fazla bilgi için [using deyimi](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` İşleci aşırı yüklenemez.  
  
 Varsa `new` işleci başarısız bellek ayırmaya, özel durum oluşturduğunda <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanılarak başlatılan `new` işleci ve ardından değerler atanır. Varsayılan ve atanan değerleri görüntülenir.  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 Varsayılan değer bir dize örneği bildiriminde `null`. Bu nedenle, bu görüntülenmez.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
