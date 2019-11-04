---
title: Anonim türler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: c6eff1cae79e7b555c5a41d10712b4f3022ff793
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419485"
---
# <a name="anonymous-types-c-programming-guide"></a>Anonim Türler (C# Programlama Kılavuzu)

Anonim türler, salt bir türü açıkça tanımlamak zorunda kalmadan tek bir nesne içinde salt okunurdur bir özellik kümesini kapsüllemek için kullanışlı bir yol sağlar. Tür adı derleyici tarafından oluşturulur ve kaynak kodu düzeyinde kullanılabilir değildir. Her özelliğin türü derleyici tarafından algılanır.  
  
 [Yeni](../../language-reference/operators/new-operator.md) işleci bir nesne başlatıcısıyla birlikte kullanarak anonim türler oluşturursunuz. Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](./object-and-collection-initializers.md).  
  
 Aşağıdaki örnek, `Amount` ve `Message`adlı iki özellik ile başlatılan anonim bir türü gösterir.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Anonim türler genellikle bir sorgu ifadesinin [Select](../../language-reference/keywords/select-clause.md) yan tümcesinde, kaynak dizisindeki her bir nesneden özelliklerin bir alt kümesini döndürmek için kullanılır. Sorgular hakkında daha fazla bilgi için bkz. [LINQ C#ın ](../../linq/index.md).  
  
 Anonim türler bir veya daha fazla genel salt okunurdur özelliği içerir. Yöntemler veya olaylar gibi başka tür sınıf üyeleri geçerli değildir. Bir özelliği başlatmak için kullanılan ifade `null`, anonim bir işlev veya bir işaretçi türü olamaz.  
  
 En yaygın senaryo, başka bir türden özelliklerle adsız bir tür başlatmalıdır. Aşağıdaki örnekte, `Product`adlı bir sınıfın var olduğunu varsayalım. Sınıf `Product`, `Color` ve `Price` özelliklerini, ilgilenmediğiniz diğer özelliklerle birlikte içerir. Değişken `products`, bir `Product` nesneleri koleksiyonudur. Anonim tür bildirimi `new` anahtar sözcüğüyle başlar. Bildirim, `Product`yalnızca iki özellik kullanan yeni bir tür başlatır. Bu, sorguda daha az miktarda veri döndürülmesine neden olur.  
  
 Anonim türde üye adları belirtmezseniz, derleyici anonim tür üyelerine onları başlatmak için kullanılan özellik ile aynı adı verir. Önceki örnekte gösterildiği gibi, ifadesiyle başlatılan bir özellik için bir ad sağlamalısınız. Aşağıdaki örnekte, anonim türün özelliklerinin adları `Color` ve `Price`.  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Genellikle, bir değişkeni başlatmak için anonim bir tür kullandığınızda değişkeni, [değişken kullanarak örtük](../../language-reference/keywords/var.md)olarak yazılmış bir yerel değişken olarak bildirirsiniz. Tür adı değişken bildiriminde belirtilemiyor, çünkü yalnızca derleyicinin adsız türdeki temel alınan ada erişimi vardır. `var`hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](./implicitly-typed-local-variables.md).  
  
 Aşağıdaki örnekte gösterildiği gibi örtük olarak yazılmış bir yerel değişkeni ve örtük olarak yazılmış bir diziyi birleştirerek anonim olarak belirlenmiş öğelerin bir dizisini oluşturabilirsiniz.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim türler [nesnesinden](../../language-reference/builtin-types/reference-types.md)doğrudan türeten ve [nesne](../../language-reference/builtin-types/reference-types.md)dışında herhangi bir türe atanamaz olan [sınıf](../../language-reference/keywords/class.md) türleridir. Derleyici her adsız tür için bir ad sağlar, ancak uygulamanız buna erişemez. Ortak dil çalışma zamanının perspektifinden, anonim bir tür diğer herhangi bir başvuru türünden farklı değildir.  
  
 Bir derlemede iki veya daha fazla anonim nesne başlatıcıları aynı sırada olan ve aynı ada ve türe sahip bir özellikler sırası belirtse, derleyici nesneleri aynı türdeki örnekler olarak değerlendirir. Derleyici tarafından oluşturulan tür bilgilerini paylaşır.  
  
 Bir alanı, özelliği, olayı veya bir yöntemin dönüş türünü anonim bir türe sahip olarak bildiremezsiniz. Benzer şekilde, bir yöntem, özellik, Oluşturucu veya dizin oluşturucunun yapısal bir parametresini anonim bir türe sahip olacak şekilde bildiremezsiniz. Anonim bir tür veya anonim türler içeren bir koleksiyonu, bir yönteme bağımsız değişken olarak geçirmek için, parametreyi tür nesnesi olarak bildirebilirsiniz. Ancak, bu işlem güçlü yazma amacını artırıyor. Sorgu sonuçlarını depolamanız veya yöntem sınırının dışında geçirmeniz gerekiyorsa, anonim bir tür yerine sıradan adlandırılmış bir yapı veya sınıf kullanmayı düşünün.  
  
 Anonim türlerdeki <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> yöntemleri, özelliklerinin `Equals` ve `GetHashCode` yöntemlerine göre tanımlandığından, aynı anonim türdeki iki örnek yalnızca tüm özellikleri eşitse eşittir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
- [C#'de LINQ Kullanmaya Başlama](/dotnet/csharp/programming-guide/concepts/linq/)
- [C# üzerinde LINQ](../../linq/index.md)
