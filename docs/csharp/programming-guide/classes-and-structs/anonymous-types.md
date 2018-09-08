---
title: Anonim Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: b732de508c8738de5e5e55168a6e17a1d88a3b02
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133171"
---
# <a name="anonymous-types-c-programming-guide"></a>Anonim Türler (C# Programlama Kılavuzu)
Anonim türleri açıkça bir tür ilk tanımlamak zorunda kalmadan tek bir nesnede salt okunur özellikler kümesi kapsüllemek için kullanışlı bir yol sağlar. Tür adı derleyici tarafından oluşturulan ve kaynak kod düzeyinde kullanılabilir değildir. Her bir özellik türü, derleyici tarafından algılanır.  
  
 Kullanarak anonim tür oluşturma [yeni](../../../csharp/language-reference/keywords/new.md) işleci birlikte bir nesne Başlatıcı. Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Aşağıdaki örnekte adlı iki özellik ile başlatılan bir anonim tür `Amount` ve `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonim türler genellikle kullanıldığı [seçin](../../../csharp/language-reference/keywords/select-clause.md) kaynak dizisindeki her bir nesneden bir özellik alt kümesi döndürmek için bir sorgu ifadesinin yan tümcesi. Sorgular hakkında daha fazla bilgi için bkz. [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Anonim türler bir veya daha fazla genel salt okunur özellikler içerir. Yöntemleri ya da olaylar gibi sınıf üyelerini diğer hiçbir tür geçerli değil. Bir özellik başlatmak için kullanılan bir ifade olamaz `null`, anonim bir işlev veya bir işaretçi türü.  
  
 Başka bir tür özellikleri içeren bir anonim tür başlatmak için en yaygın senaryodur bakın. Aşağıdaki örnekte, bir sınıf adlı bulunduğunu varsayar `Product`. Sınıf `Product` içerir `Color` ve `Price` ilginizi olmayan diğer özellikleri birlikte özellikleri. Değişken `products` koleksiyonudur `Product` nesneleri. Anonim tür bildirimi ile başlayan `new` anahtar sözcüğü. Yalnızca iki özelliklerinden kullanan yeni bir türü bildirimini başlatır `Product`. Bu, daha küçük bir sorguda döndürülecek veri miktarı neden olur.  
  
 Anonim türdeki üye adları belirtmezseniz, derleyici bunları başlatmak için kullanılan özellik adıyla aynı anonim türdeki üyeleri sağlar. Önceki örnekte gösterilen şekilde bir ifadeyle başlatılan bir özellik için bir ad sağlamanız gerekir. Aşağıdaki örnekte, anonim tür özelliklerini adlarıdır `Color` ve `Price`.  
  
 [!code-csharp[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 Bir değişkeni başlatmak için anonim bir tür kullandığınızda, genellikle, değişken türü örtük olarak belirlenmiş yerel değişken olarak kullanarak bildirdiğiniz [var](../../../csharp/language-reference/keywords/var.md). Yalnızca derleyicinin erişim anonim tür temel adına sahip olduğundan Değişken bildiriminde tür adı belirtilemez. Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Aşağıdaki örnekte gösterildiği gibi bir türü örtük olarak belirlenmiş yerel değişken ve örtük olarak belirlenmiş dizi birleştirerek anonim olarak belirlenmiş öğeleri dizisi oluşturabilirsiniz.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim türler [sınıfı](../../../csharp/language-reference/keywords/class.md) doğrudan öğesinden türetilen türler [nesne](../../../csharp/language-reference/keywords/object.md), ve dışında herhangi bir türe yayımlanamıyorsa [nesne](../../../csharp/language-reference/keywords/object.md). Derleyici, uygulamanıza erişemez ancak her anonim bir tür için bir ad sağlar. Ortak dil çalışma zamanı açısından bakıldığında, anonim bir tür başka bir başvuru türünden farklı değildir.  
  
 İki veya daha fazla anonim nesne başlatıcıları bir derleme, aynı sırayla ve aynı adlarını ve türlerini sahip özellikler bir dizi belirtirseniz, derleyicinin nesneleri aynı türde bir örnek değerlendirir. Aynı derleyici tarafından oluşturulan tür bilgilerini paylaşırlar.  
  
 Bir alan, özellik, bir olay veya anonim bir tür olarak bir yöntemin dönüş türünü bildiremezsiniz. Benzer şekilde, bir yöntemi, özelliği, oluşturucuya veya anonim bir tür olarak dizin oluşturucu bir biçimsel parametresi bildiremez. Anonim bir tür veya anonim türler bir yöntemi için bağımsız değişken olarak içeren bir koleksiyona geçmek için parametre türü nesnesi olarak bildirebilirsiniz. Ancak, bunun yapılması, güçlü yazım amacını boşa çıkarır. Sorgu sonuçlarını depolamak veya bunları yöntemi sınırının dışına geçirmek yerine anonim bir tür bir sıradan adlandırılmış yapı ya da sınıf kullanmayı düşünün.  
  
 Çünkü <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemlerin anonim türleri açısından tanımlandığı `Equals` ve `GetHashCode` iki örneği aynı anonim tür özellikleri yöntemlerdir tüm özellikleri eşitse eşit.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [C#'de LINQ Kullanmaya Başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
