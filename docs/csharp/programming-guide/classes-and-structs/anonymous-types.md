---
title: Anonim Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 24ebf1c98e14eaf74572a6143ea6865d89735a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-types-c-programming-guide"></a>Anonim Türler (C# Programlama Kılavuzu)
Anonim türleri açıkça bir tür ilk tanımlamak zorunda kalmadan bir salt okunur özellikler kümesi tek bir nesnede kapsüllemek için kolay bir yol sağlamak. Tür adı derleyici tarafından üretilen ve kaynak kodu düzeyinde kullanılabilir değildir. Her bir özellik türü derleyici tarafından algılanır.  
  
 Anonim türler kullanarak oluşturduğunuz [yeni](../../../csharp/language-reference/keywords/new.md) nesne Başlatıcı birlikte işleci. Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Aşağıdaki örnek adlı iki özelliklerle başlatılmış olan anonim bir tür gösterir `Amount` ve `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonim türleri genelde kullanıldığı [seçin](../../../csharp/language-reference/keywords/select-clause.md) özelliklerinin bir alt kaynak dizisindeki her nesne döndürmek için bir sorgu ifadesi yan tümcesi. Sorgular hakkında daha fazla bilgi için bkz: [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Anonim türler bir veya daha fazla genel salt okunur özellikler içerir. Herhangi bir yöntemleri ya da olaylar gibi sınıf üyeleri türleri geçerlidir. Bir özellik başlatmak için kullanılan ifade olamaz `null`, adsız bir işlev veya bir işaretçi türü.  
  
 Başka bir türünden özelliklere sahip anonim bir tür başlatmak için en yaygın senaryodur bakın. Aşağıdaki örnekte, bir sınıf adlı var olduğunu varsayar `Product`. Sınıf `Product` içeren `Color` ve `Price` ilgilendiğiniz olmayan diğer özellikleri ile birlikte özellikleri. Değişken `products` koleksiyonudur `Product` nesneleri. Anonim tür bildirimi ile başlayan `new` anahtar sözcüğü. Yalnızca iki özelliklerinden kullanan yeni bir türü bildirimini başlatır `Product`. Bu, daha küçük bir sorguda döndürülecek veri miktarı neden olur.  
  
 Anonim türdeki üye adlarının belirtmezseniz derleyici anonim tür üyeleri bunları başlatmak için kullanılan özellik aynı adı sağlar. Önceki örnekte gösterildiği gibi bir ifade ile başlatılmış bir özellik için bir ad sağlamanız gerekir. Aşağıdaki örnekte, anonim tür özelliklerini adlarıdır `Color` ve `Price`.  
  
 [!code-csharp[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 Bir değişken başlatmak için anonim bir tür kullandığınızda, genellikle, değişken türü örtük olarak belirlenmiş yerel değişken olarak kullanarak bildirdiğiniz [var](../../../csharp/language-reference/keywords/var.md). Yalnızca derleyici anonim tür, temel alınan adına erişim izni olduğundan Değişken bildiriminde tür adı belirtilemez. Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Aşağıdaki örnekte gösterildiği gibi bir türü örtük olarak belirlenmiş yerel değişken ve türü örtük olarak belirlenmiş bir dizi birleştirerek anonim olarak yazılan öğeleri dizisi oluşturabilirsiniz.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim türler [sınıfı](../../../csharp/language-reference/keywords/class.md) doğrudan öğesinden türetilen türler [nesne](../../../csharp/language-reference/keywords/object.md), ve, olamaz dönüştürülür dışında herhangi bir tür için [nesne](../../../csharp/language-reference/keywords/object.md). Uygulamanız bu verilere erişemez rağmen derleyici anonim her tür için bir ad sağlar. Ortak dil çalışma zamanı perspektifinden anonim bir tür başka bir başvuru türünden farklı değildir.  
  
 İki veya daha fazla anonim nesne başlatıcıları derlemedeki aynı sırada olan ve aynı adlara ve türleri olan özellikler dizisi belirtirseniz, derleyici nesneleri aynı türde bir örnek değerlendirir. Bunlar aynı derleyicinin ürettiği türü bilgileri paylaşın.  
  
 Bir alan, bir özellik, bir olay veya anonim bir tür olarak bir yöntemin dönüş türünü bildiremezsiniz. Benzer şekilde, biçimsel parametresi bir yöntemi, özelliği, oluşturucunun ya da anonim bir tür olarak dizin oluşturucuyu bildiremezsiniz. Anonim bir tür ya da bir yöntemi için bağımsız değişken olarak anonim türler içeren bir koleksiyon geçirmek için parametre türü nesnesi olarak bildirebilirsiniz. Ancak, bunun yapılması güçlü yazım uramayacak. Sorgu sonuçları deposunu veya yöntemi sınırının dışında geçmesi gerekir, anonim bir tür yerine bir sıradan adlandırılmış yapı ya da sınıf kullanmayı düşünün.  
  
 Çünkü <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anonim türler yöntemlere cinsinden tanımlanır `Equals` ve `GetHashCode` özellikleri, aynı anonim tür iki örneğini yöntemlerdir yalnızca tüm özelliklerini eşitse eşit.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
