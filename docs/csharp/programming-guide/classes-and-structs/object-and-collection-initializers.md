---
title: Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: def33041c4202c80aad9f08d1ff8d9dbbc477061
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780055"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)
Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır. Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.  Aşağıdaki örnek, adlandırılmış bir türü ile bir nesne Başlatıcı kullanma işlemi gösterilmektedir `Cat` ve varsayılan oluşturucunun nasıl çağrılacağını. Otomatik uygulanan özelliklerin kullanımına dikkat edin `Cat` sınıfı. Daha fazla bilgi için [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
Nesne Başlatıcı sözdizimi örneği oluşturmanıza olanak sağlar ve sonra kendi atanan özelliklere sahip yeni oluşturulan nesne değişkeni ataması atar.
  
## <a name="object-initializers-with-anonymous-types"></a>Anonim türlerde Nesne Başlatıcıları  
 Nesne başlatıcıları her bağlamda kullanılabilir olsa da, bunlar özellikle kullanışlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde. Sorgu ifadeleri, sık sık kullanırlar [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), hangi yalnızca başlatılabilir bir nesne Başlatıcı kullanarak aşağıdaki bildirimde gösterildiği gibi.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Anonim türler etkinleştirme `select` yan tümcesinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu deyimi orijinal sıranın nesnelerini değeri ve şekli orijinalden farklı olabilir nesneleri dönüştürün. Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır. Aşağıdaki örnekte, varsayımında bir ürün nesnesinin (`p`) birçok alan ve yöntem içerir ve, yalnızca sırası oluşturmakla ilgili bilgi sahibi olduğunuz ürün adını ve birim fiyatı içerir.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Bu sorgu yürütüldüğünde `productInfos` değişkeni erişilebilen bir nesne sırası içerecektir bir `foreach` Bu örnekte gösterildiği gibi deyimi:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Yeni anonim türdeki her bir nesnenin, orijinal nesnedeki özelliklerle veya alanlarla aynı adları alan iki genel özelliği vardır. Ayrıca, anonim bir tür oluştururken bir alanı yeniden adlandırabilirsiniz; Aşağıdaki örnek yeniden adlandırır `UnitPrice` alanı `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a>Koleksiyon başlatıcıları  
 Koleksiyon başlatıcıları bir belirtmenize olanak tanır veya daha fazla öğe başlatıcıları bir koleksiyon başlattığınızda uygulayan türü <xref:System.Collections.IEnumerable> ve `Add` uygun imzalı bir örnek yöntemi veya bir genişletme yöntemi olarak. Öğe başlatıcıları basit bir değer, bir ifade veya bir nesne başlatıcı olabilir. Koleksiyon Başlatıcısı kullanarak, birden çok çağrı belirtmeniz gerekmez `Add` ; kaynak kodunuzdaki sınıfın yöntemi derleyici çağrıları ekler.  
  
 Aşağıdaki örnekler, iki basit koleksiyon başlatıcısını gösterir:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 Aşağıdaki koleksiyon Başlatıcısı nesnelerini başlatmak için nesne başlatıcıları kullanır `Cat` önceki bir örnekte tanımlanan sınıfı. Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Belirtebileceğiniz [null](../../../csharp/language-reference/keywords/null.md) bir koleksiyon başlatıcısında bir öğe olarak varsa koleksiyonun `Add` yöntemi sağlar.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Koleksiyon dizin oluşturma destekliyorsa öğeleri dizine belirtebilirsiniz.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a>Örnekler

 Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 Uygulayan bir nesne aşağıdaki örnekte gösterilen <xref:System.Collections.IEnumerable> içeren bir `Add` imzasıiçinkarşılıkgelenöğebaşınabirdençoköğeiçerenkoleksiyonbaşlatıcılarıyöntemiilebirdençokparametresağlar`Add` yöntemi. 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 `Add` yöntemleri kullanabilir `params` aşağıdaki örnekte gösterildiği gibi değişken sayıda bağımsız değişken almak için anahtar sözcüğü. Bu örnekte, dizinleri kullanarak bir koleksiyonu başlatmak için bir dizin oluşturucu de özel uygulanışı gösterilmektedir.
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
