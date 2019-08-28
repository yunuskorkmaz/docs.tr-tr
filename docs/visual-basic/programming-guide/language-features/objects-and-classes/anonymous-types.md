---
title: Anonim Türleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 2d134b8c8ef202a91b35ad8645bf63622b5e8030
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040838"
---
# <a name="anonymous-types-visual-basic"></a>Anonim Türleri (Visual Basic)
Visual Basic, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanıza olanak sağlayan anonim türleri destekler. Bunun yerine, derleyici sizin için bir sınıf oluşturur. Sınıfın kullanılabilir bir adı yoktur, doğrudan öğesinden <xref:System.Object>devralır ve nesneyi bildirirken belirttiğiniz özellikleri içerir. Veri türünün adı belirtilmediğinden, *anonim tür*olarak adlandırılır.  
  
 Aşağıdaki örnek, `product` `Name` ve `Price`iki özelliği olan anonim bir türün bir örneği olarak değişkenini bildirir ve oluşturur.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 *Sorgu ifadesi* , bir sorgu tarafından seçilen veri sütunlarını birleştirmek için anonim türler kullanır. Belirli bir sorgunun seçim olabileceği sütunları tahmin edemediği için sonucun türünü önceden tanımlayamazsınız. Anonim türler, herhangi bir sırada herhangi bir sayıda sütun seçen bir sorgu yazmanızı sağlar. Derleyici, belirtilen özelliklerle ve belirtilen sırada eşleşen bir veri türü oluşturur.  
  
 Aşağıdaki örneklerde `products` , her birinin çok sayıda özelliği olan ürün nesnelerinin bir listesidir. Değişken `namePriceQuery` , yürütüldüğünde, iki `Name` özelliği `Price`olan anonim bir türün örnek koleksiyonunu döndüren bir sorgunun tanımını tutar.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 Değişken `nameQuantityQuery` , yürütüldüğünde, iki `Name` özelliği `OnHand`olan anonim bir türün örnek koleksiyonunu döndüren bir sorgunun tanımını tutar.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Anonim bir tür için derleyici tarafından oluşturulan kod hakkında daha fazla bilgi için bkz. [anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
> Anonim türün adı derleyici tarafından oluşturulmuştur ve derlemeden derlemeye farklılık gösterebilir. Bir proje yeniden derlenmeye çalışılırken ad değiştirebileceğinden, kodunuz anonim bir türün adını kullanmamalıdır veya bu adı kullanmamalıdır.  
  
## <a name="declaring-an-anonymous-type"></a>Anonim bir tür bildirme  
 Anonim bir türün bir örneğinin bildirimi, türün özelliklerini belirtmek için bir başlatıcı listesi kullanır. Yöntemler veya olaylar gibi diğer sınıf öğelerini değil, anonim bir tür bildirdiğinizde yalnızca özellikleri belirtebilirsiniz. Aşağıdaki örnekte, `product1` iki özelliği olan anonim bir türün örneğidir: `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Özellikleri anahtar özellikler olarak tanımlarsanız, bunları eşitlik için iki anonim tür örneğini karşılaştırmak üzere kullanabilirsiniz. Ancak, anahtar özelliklerinin değerleri değiştirilemez. Daha fazla bilgi için bu konunun devamındaki temel Özellikler bölümüne bakın.  
  
 Anonim bir türün bir örneğini bildirmenin, bir nesne Başlatıcısı kullanarak adlandırılmış türde bir örnek bildirme gibidir:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Anonim tür özelliklerini belirtmek için diğer yollar hakkında daha fazla bilgi için bkz [. nasıl yapılır: Anonim tür bildirimlerinde](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)özellik adlarını ve türleri çıkarçıkar.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özellikleri, anahtar olmayan özelliklerden çeşitli temel yollarla farklılık gösterir:  
  
- İki örneğinin eşit olup olmadığını belirleyebilmek için yalnızca anahtar özelliklerinin değerleri karşılaştırılır.  
  
- Anahtar özelliklerinin değerleri salt okunurdur ve değiştirilemez.  
  
- Anonim bir tür için derleyici tarafından oluşturulan karma kodu algoritmasına yalnızca anahtar özellik değerleri dahildir.  
  
### <a name="equality"></a>Eşitlik  
 Anonim türlerin örnekleri, yalnızca aynı anonim türdeki örneklerle eşit olabilir. Derleyici, aşağıdaki koşulları karşılıyorsa iki örneği aynı türde örnekler olarak değerlendirir:  
  
- Aynı derlemede bildirilmiştir.  
  
- Özellikleri aynı ada, aynı gösterilen türlere sahiptir ve aynı sırada bildirilmiştir. Ad karşılaştırmaları büyük/küçük harfe duyarlı değildir.  
  
- Her birinde aynı Özellikler anahtar özellikler olarak işaretlenir.  
  
- Her bildirimdeki en az bir özellik bir anahtar özelliktir.  
  
 Anahtar özellikleri olmayan anonim türlerin bir örneği yalnızca kendi kendine eşittir.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Anahtar özelliklerinin değerleri eşitse aynı anonim türdeki iki örnek eşittir. Aşağıdaki örneklerde, eşitlik nasıl test edileceği gösterilmektedir.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Salt okunurdur değerler  
 Anahtar özelliklerinin değerleri değiştirilemez. Örneğin `prod8` , önceki örnekte `Price` `Name` , ve alanları `read-only`, ancak `OnHand` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Sorgu Ifadelerinden anonim türler  
 Sorgu ifadeleri her zaman anonim türlerin oluşturulmasını gerektirmez. Mümkün olduğunda, sütun verilerini tutmak için mevcut bir tür kullanır. Bu, sorgu veri kaynağından tam kayıtlar veya her bir kayıttaki tek bir alan döndürdüğünde oluşur. Aşağıdaki kod örneklerinde, `customers` bir `Customer` sınıfın nesnelerinin bir koleksiyonudur. Sınıfında birçok özellik bulunur ve sorgu sonucuna bir veya daha fazlasını istediğiniz sırada dahil edebilirsiniz. İlk iki örnekte, sorgular adlandırılmış türdeki öğeleri seçtiğinden hiçbir anonim tür gerekmez:  
  
- `custs1`bir dize olduğundan, `cust.Name` dizeler koleksiyonunu içerir.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2`Her `Customer` öğesibir`Customer` nesne olduğu ve sorgu tarafından tüm öğe seçildiği için nesne koleksiyonunu içerir. `customers`  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Ancak, uygun adlandırılmış türler her zaman kullanılabilir değildir. Müşteri adlarını ve adreslerini bir amaç için, müşteri KIMLIĞI numaralarını ve diğer konumları, üçüncü için müşteri adlarını, adresleri ve sıra geçmişlerini seçmek isteyebilirsiniz. Anonim türler, herhangi bir sırada her türlü özelliği, sonucu tutmak için yeni bir adlandırılmış tür bildirmeksizin seçmenizi sağlar. Bunun yerine, derleyici her bir özellik derlemesi için anonim bir tür oluşturur. Aşağıdaki sorgu, içindeki `Customer` `customers`her bir nesneden yalnızca müşterinin adını ve kimlik numarasını seçer. Bu nedenle, derleyici yalnızca bu iki özelliği içeren anonim bir tür oluşturur.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Anonim türdeki özelliklerin adları ve veri türleri `Select`, ve `cust.ID`' `cust.Name` den bağımsız değişkenlerden alınır. Bir sorgu tarafından oluşturulan anonim türdeki özellikler her zaman önemli özelliklerdir. Aşağıdaki döngüde yürütüldüğünde `Name` sonuç, ikianahtarözelliklerinesahipanonimbirtürünörneklerininbirkoleksiyonudur.`ID` `For Each` `custs3`  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Tarafından `custs3` temsil edilen koleksiyondaki öğeler kesin olarak türdedir ve kullanılabilir özellikler arasında gezinmek ve türlerini doğrulamak için IntelliSense 'i kullanabilirsiniz.  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Anonim türleri kullanıp kullanmayacağınızı karar verme  
 Bir anonim sınıfın örneği olarak bir nesnesi oluşturmadan önce, bunun en iyi seçenek olup olmadığını göz önünde bulundurun. Örneğin, ilgili verileri içeren geçici bir nesne oluşturmak isterseniz ve tüm bir sınıfın içerebileceği diğer alan ve yöntemlere ihtiyacınız yoksa, anonim bir tür iyi bir çözümdür. Anonim türler, her bildirim için farklı bir özellikler seçimi isterseniz veya özelliklerin sırasını değiştirmek istiyorsanız da kullanışlıdır. Ancak, projeniz aynı özelliklere sahip çeşitli nesneler içeriyorsa, sabit bir siparişte, bir sınıf Oluşturucusu ile adlandırılmış bir tür kullanarak bunları daha kolay bir şekilde bildirebilirsiniz. Örneğin, uygun bir oluşturucuyla, bir sınıfın birden fazla örneğini bildirmek daha kolaydır, bu `Product` da bir anonim türün birkaç örneğini bildirmektedir.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Adlandırılmış türlerin başka bir avantajı, derleyicinin bir özellik adının yanlışlıkla yanlış yazılanı yakalayabiliyor olması olabilir. Önceki örneklerde `firstProd2` `secondProd2`,, ve `thirdProd2` aynı anonim türdeki örnekler olmak üzere tasarlanmıştır. Ancak, aşağıdaki yollarla yanlışlıkla bir şekilde bildirirseniz `thirdProd2` , türü `firstProd2` ve `secondProd2`' den farklı olur.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Daha da önemlisi, adlandırılmış türlerin örneklerine uygulanmayan anonim türlerin kullanımıyla ilgili sınırlamalar vardır. `firstProd2`, `secondProd2`, ve `thirdProd2` aynı anonim türdeki örneklerdir. Ancak, paylaşılan anonim türün adı kullanılabilir değildir ve kodunuzda bir tür adının beklendiği yerde yer alamaz. Örneğin, bir anonim tür, başka bir değişken veya alan bildirmek için ya da herhangi bir tür bildiriminde bir yöntem imzası tanımlamak için kullanılamaz. Sonuç olarak, yöntemler arasında bilgi paylaşmanız gerektiğinde anonim türler uygun değildir.  
  
## <a name="an-anonymous-type-definition"></a>Anonim tür tanımı  
 Anonim türdeki bir örneğin bildirimine yanıt olarak, derleyici belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.  
  
 Anonim tür en az bir anahtar özellik <xref:System.Object>içeriyorsa, tanım öğesinden devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. Eşitliği test etmek ve karma kod değerini belirlemek için üretilen kod yalnızca anahtar özelliklerini dikkate alır. Anonim tür hiçbir anahtar özelliği içermiyorsa, yalnızca <xref:System.Object.ToString%2A> geçersiz kılınır. Anonim bir türün açıkça adlandırılmış özellikleri, oluşturulan bu yöntemlerle çakışamaz. Diğer bir deyişle,,, `.Equals`veya `.GetHashCode` `.ToString` özelliğini kullanamazsınız.  
  
 En az bir anahtar özelliği olan anonim tür tanımları <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimini de uygular, burada `T` anonim türün türüdür.  
  
 Derleyici tarafından oluşturulan kod ve geçersiz kılınan yöntemlerin işlevselliği hakkında daha fazla bilgi için bkz. [anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Anonim tür bildirimlerinde özellik adlarını ve türleri çıkarçıkar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonim Tip Tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
