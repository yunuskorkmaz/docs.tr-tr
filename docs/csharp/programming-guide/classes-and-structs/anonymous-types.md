---
title: Anonim Türleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 63bc5560ba19ff36764465a6b89b81c13beec97a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170344"
---
# <a name="anonymous-types-c-programming-guide"></a>Anonim Türler (C# Programlama Kılavuzu)

Anonim türler, önce açıkça bir tür tanımlamak zorunda kalmadan, salt okunur özellikleri kümesini tek bir nesneye kapsüllemek için kullanışlı bir yol sağlar. Tür adı derleyici tarafından oluşturulur ve kaynak kodu düzeyinde kullanılamaz. Her özelliğin türü derleyici tarafından çıkarılır.  
  
 [Yeni](../../language-reference/operators/new-operator.md) işleci bir nesne başlatma ile birlikte kullanarak anonim türleri oluşturursunuz. Nesne baş harfleri hakkında daha fazla bilgi için [Object ve Collection Initializers'a](./object-and-collection-initializers.md)bakın.  
  
 Aşağıdaki örnek, adlı `Amount` iki özellik ile başharfe `Message`bürünen anonim bir türü gösterir ve .  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Adsız türler genellikle kaynak sıradaki her nesneden özelliklerin bir alt kümesini döndürmek için sorgu ifadesinin [seçme](../../language-reference/keywords/select-clause.md) yan tümcesinde kullanılır. Sorgular hakkında daha fazla bilgi için [C# 'daki LINQ'ya](../../linq/index.md)bakın.  
  
 Anonim türler, herkese açık bir veya daha fazla genel okuma özelliği içerir. Yöntem veya olaylar gibi başka sınıf üyeleri geçerli değildir. Bir özelliği niçin başlatılması için kullanılan `null`ifade, anonim bir işlev veya işaretçi türü olamaz.  
  
 En yaygın senaryo, başka bir türözellikleri ile anonim bir tür başlatılmasıdır. Aşağıdaki örnekte, adı geçen `Product`bir sınıfın var olduğunu varsayalım. `Product` Sınıf, `Color` `Price` ilgilenmediğiniz diğer özelliklerle birlikte özellikleri içerir. Değişken `products` `Product` nesnelerin bir koleksiyondur. Anonim tür bildirimi anahtar `new` sözcük ile başlar. Bildirim, 'den `Product`yalnızca iki özellik kullanan yeni bir tür baş harflerini Bu, sorguda döndürülecek daha az miktarda veri neden olur.  
  
 Anonim türde üye adlar belirtmezseniz, derleyici anonim tür üyelerine onları başlatmada kullanılan özellik ile aynı adı verir. Önceki örnekte gösterildiği gibi, bir ifadeyle başharfe başlatılmakta olan bir özellik için bir ad sağlamanız gerekir. Aşağıdaki örnekte, anonim türdeki özelliklerin adları `Color` `Price`ve .  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Tipik olarak, bir değişkeni başlatmak için anonim bir tür kullandığınızda, [değişkeni var](../../language-reference/keywords/var.md)kullanarak örtülü olarak yazılan yerel değişken olarak beyan esiniz. Yalnızca derleyici anonim türün altadı adına erişebildiği için tür adı değişken bildiriminde belirtilemez. Hakkında `var`daha fazla bilgi için bkz: [Örtülü Olarak Yazılan Yerel Değişkenler.](./implicitly-typed-local-variables.md)  
  
 Aşağıdaki örnekte gösterildiği gibi, örtük olarak yazılan yerel değişkeni ve örtülü olarak yazılan bir diziyi birleştirerek anonim olarak yazılan öğeler den oluşan bir dizi oluşturabilirsiniz.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Anonim türleri doğrudan [nesneden](../../language-reference/builtin-types/reference-types.md)türetilen sınıf [türleridir](../../language-reference/keywords/class.md) ve [nesne](../../language-reference/builtin-types/reference-types.md)dışında herhangi bir türe atılamaz. Derleyici, uygulamanız erişemese de her anonim tür için bir ad sağlar. Ortak dil çalışma zamanı açısından bakıldığında, anonim bir tür diğer başvuru türünden farklı değildir.  
  
 Bir derlemedeki iki veya daha fazla anonim nesne başharfi aynı sırada olan ve aynı ad ve türe sahip özellikler dizisi belirtirse, derleyici nesneleri aynı türdeki örnekler olarak sıralar. Aynı derleyici tarafından oluşturulan tür bilgilerini paylaşırlar.  
  
 Bir alanı, bir özelliği, olayı veya bir yöntemin dönüş türünü anonim bir türe sahip olarak beyan edemezsiniz. Benzer şekilde, bir yöntemin, özelliğin, oluşturucunun veya dizinleyicinin resmi bir parametresini anonim bir türe sahip olarak beyan edemezsiniz. Anonim bir türü veya anonim türleri içeren bir koleksiyonu bir yönteme bağımsız değişken olarak geçirmek için, parametreyi tür nesnesi olarak bildirebilirsiniz. Ancak, bunu yapmak güçlü yazma amacı nı yener. Sorgu sonuçlarını depolamanız veya yöntem sınırının dışına geçmeniz gerekiyorsa, anonim bir tür yerine sıradan bir adlandırılmış yapı veya sınıf kullanmayı düşünün.  
  
 Anonim <xref:System.Object.Equals%2A> türlerdeki yöntemler ve <xref:System.Object.GetHashCode%2A> yöntemler özelliklerin `Equals` `GetHashCode` yöntemleri ve yöntemleri açısından tanımlandığından, aynı anonim türdeki iki örnek yalnızca tüm özellikleri eşitse eşittir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
- [C#'de LINQ'e Başlarken](../concepts/linq/index.md)
- [C# üzerinde LINQ](../../linq/index.md)
