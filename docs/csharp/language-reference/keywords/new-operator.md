---
title: new İşleci (C# Başvurusu)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268927"
---
# <a name="new-operator-c-reference"></a>new İşleci (C# Başvurusu)
Nesneleri oluşturmak ve oluşturucular çağırmak için kullanılır. Örneğin:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 Anonim türler örneklerini oluşturmak için de kullanılır:  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` İşleci değer türleri için varsayılan oluşturucu çağırmak için de kullanılır. Örneğin:  
  
```csharp
int i = new int();  
```  
  
 Önceki deyiminde `i` için başlatılan `0`, türü için varsayılan değeri olduğu `int`. Deyim şu aynı etkiye sahiptir:  
  
```csharp
int i = 0;  
```  
  
 Varsayılan değerlerin tam listesi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 İçin varsayılan bir oluşturucu bildirmek için bir hata olduğunu unutmayın bir [yapısı](../../../csharp/language-reference/keywords/struct.md) her değer türü örtük olarak ortak varsayılan bir oluşturucu olduğundan. Parametreli oluşturucular ilk değerlerini ayarlamak için bir yapı türüne bildirmeniz mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekli ise gereklidir.  
  
 Yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak yok edilir, ancak içeren bağlamları kaldırıldığı zaman başvuru türü nesneler tarafından çöp yok ancak değer türü nesneleri yok Toplayıcı bunları son referansı kaldırıldıktan sonra belirtilmeyen bir zaman. Dosya tanıtıcıları ya da ağ bağlantıları gibi kaynakları içeren türleri içerdikleri kaynaklara mümkün olan en kısa sürede yayımlanan emin olmak için belirleyici temizleme kullanmayı tercih edilir. Daha fazla bilgi için bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` İşleci olamaz aşırı yüklenebilir.  
  
 Varsa `new` işleci başarısız bellek ayıramadı, özel durum oluşturur <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanarak başlatılmış `new` işleci ve değerler atanır. Varsayılan ve atanmış değerler görüntülenir.  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 Varsayılan değer bir dize örneği bildiriminde `null`. Bu nedenle, görüntülenmez.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
