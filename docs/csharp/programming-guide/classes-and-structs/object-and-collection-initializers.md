---
title: "Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7445a2919baaa477b4611c4c5ee5a0031539ca30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)
Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır. Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.  Aşağıdaki örnekte bir adlandırılmış türüyle nesne Başlatıcı kullanmayı gösterir `Cat` ve varsayılan oluşturucu çağırmak nasıl. Otomatik uygulanan özellikler kullanımına dikkat edin `Cat` sınıfı. Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
Nesne başlatıcıları sözdizimi örneği oluşturmanıza olanak tanır ve bundan sonra değişken ataması atanan özelliklerini ile yeni oluşturulan nesnenin atar.
  
## <a name="object-initializers-with-anonymous-types"></a>Anonim türlerde Nesne Başlatıcıları  
 Nesne başlatıcıları herhangi bir bağlamda kullanılır ancak bunlar özellikle kullanışlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri. Sorgu ifadeleri olun, sık kullanılan [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), hangi yalnızca başlatılabilir nesne Başlatıcı kullanarak aşağıdaki bildiriminde gösterildiği gibi.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Anonim türler etkinleştirmek `select` yan tümcesinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesi, değer ve şekli özgün değişebilir nesneler özgün sırasının nesnelerini dönüştürür. Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır. Aşağıdaki örnekte, varsayımında bir product nesnesi (`p`) birçok alanları ve yöntemleri içerir ve, yalnızca nesnelerinin bir dizisi oluşturmada ilgilendiğiniz ürün adı ve birim fiyat içerebilir.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Bu sorgunun yürütüldüğü zaman `productInfos` değişkeni erişilebilen nesnelerinin bir dizisi içerecek bir `foreach` Bu örnekte gösterildiği gibi deyimi:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Yeni anonim türdeki her bir nesnenin, orijinal nesnedeki özelliklerle veya alanlarla aynı adları alan iki genel özelliği vardır. Anonim bir tür oluştururken bir alanı de yeniden adlandırabilirsiniz; Aşağıdaki örnekte yeniden adlandırır `UnitPrice` alanı `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a>Boş değer atanabilir tiplerde Nesne Başlatıcıları  
 Bir nesne başlatıcısını null yapılabilir bir yapıyla birlikte kullanmak bir derleme zamanı hatasıdır.  
  
## <a name="collection-initializers"></a>Koleksiyon başlatıcıları  
 Koleksiyon başlatıcıları birini belirtmenize olanak tanır veya bu uygulayan bir koleksiyon başlattığınızda daha fazla öğesi başlatıcıları yazın <xref:System.Collections.IEnumerable> ve `Add` uygun imzalı bir örnek yöntemi veya bir genişletme yöntemi olarak. Öğe başlatıcıları basit bir değer, bir ifade veya bir nesne başlatıcı olabilir. Koleksiyon Başlatıcısı kullanarak, birden fazla çağrı belirtmek zorunda değilsiniz `Add` kaynak kodunuzu; sınıfının yöntemi çağrıları derleyici ekler.  
  
 Aşağıdaki örnekler, iki basit koleksiyon başlatıcısını gösterir:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 Aşağıdaki koleksiyon Başlatıcısı nesnelerin başlatmak için nesne başlatıcıları kullanan `Cat` bir önceki örnekte tanımlanan sınıfı. Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Belirleyebileceğiniz [null](../../../csharp/language-reference/keywords/null.md) koleksiyon başlatıcısı bir öğe olarak durumunda koleksiyonun `Add` yöntemi sağlar.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Toplama dizin oluşturmayı destekliyorsa öğeleri dizine belirtebilirsiniz.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
