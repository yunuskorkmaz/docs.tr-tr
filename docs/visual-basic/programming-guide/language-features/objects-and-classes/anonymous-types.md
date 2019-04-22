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
ms.openlocfilehash: 3dc2083e5b4fd06250a1387c32f0eba28e879b30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829141"
---
# <a name="anonymous-types-visual-basic"></a>Anonim Türleri (Visual Basic)
Visual Basic nesne veri türü için bir sınıf tanımı yazmaya gerek kalmadan oluşturmanıza olanak sağlayan anonim türler destekler. Bunun yerine, derleyici bir sınıf sizin için oluşturur. Kullanılabilir adı yok, doğrudan devralan sınıf <xref:System.Object>ve nesneyi bildirirken belirttiğiniz özellikleri içeriyor. Veri türünün adı belirtilmediğinden bu şeklinde adlandırılan bir *anonim tür*.  
  
 Aşağıdaki örnek bildirir ve değişken oluşturur `product` iki özelliğe sahiptir anonim bir türün bir örneği olarak `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 A *sorgu ifadesi* anonim tür bir sorgu tarafından seçmiş veri sütunlarının birleştirmek için kullanır. Belirli bir sorgu seçebilirsiniz sütunları tahmin edemezsiniz çünkü önceden sonuç türü tanımlayamazsınız. Anonim türler, herhangi bir sırada herhangi bir sayıda sütun seçen bir sorgu yazmak etkinleştirin. Derleyicinin, belirtilen özellikleri ve belirtilen sırayla eşleşen bir veri türü oluşturur.  
  
 Aşağıdaki örneklerde, `products` ürün nesnelerin her biri sahip birçok özellik listesini içerir. Değişken `namePriceQuery` yürütüldüğünde, iki özelliğe sahiptir anonim bir türün örneklerinin bir koleksiyonunu döndüren bir sorgu tanımını tutan `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 Değişken `nameQuantityQuery` yürütüldüğünde, iki özelliğe sahiptir anonim bir türün örneklerinin bir koleksiyonunu döndüren bir sorgu tanımını tutan `Name` ve `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Anonim bir tür için derleyici tarafından oluşturulan kod hakkında daha fazla bilgi için bkz: [anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Derleyici, oluşturulan ve derleme başka bir derleme değişebilir anonim tür adıdır. Kodunuzu kullanın veya bir proje derlendiğinde adı değişebileceğinden anonim bir türün adına dayanan gerekir.  
  
## <a name="declaring-an-anonymous-type"></a>Anonim bir tür bildirme  
 Anonim bir türün bir örneği bildirimi başlatıcı listesi türünün özelliklerini belirtmek için kullanır. Anonim bir tür, yöntemler veya olayları gibi diğer sınıfı öğelerini değil, bildirdiğiniz seçtiğinizde yalnızca özelliklerini belirtebilirsiniz. Aşağıdaki örnekte, `product1` iki özelliğe sahiptir anonim bir türün bir örneği: `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Özellikleri anahtar özellik olarak belirlerseniz, eşitlik için iki anonim tür örnekleri karşılaştırmak için kullanabilirsiniz. Ancak, anahtar özelliklerin değerlerini değiştirilemez. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde anahtar özellikler bölümüne bakın.  
  
 Anonim bir türün bir örneği bildirme adlandırılmış bir türün bir örneğini bir nesne Başlatıcı kullanarak bildirme gibi olduğuna dikkat edin:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Anonim tür özelliklerini belirtmek için diğer yollar hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özellikleri anahtar olmayan özelliklerinden birkaç temel farklar:  
  
-   Yalnızca anahtar özelliklerin değerlerini iki örneğinin eşit olup olmadığını belirlemek üzere karşılaştırılır.  
  
-   Anahtar özelliklerin değerlerini salt okunurdur ve değiştirilemez.  
  
-   Yalnızca anahtar özellik değerlerini anonim bir tür için karma derleyicinin ürettiği kodu algoritmasını dahil edilmiştir.  
  
### <a name="equality"></a>Eşitlik  
 Anonim türlerin örnekleri aynı anonim türdeki örneklerin yalnızca olmaları durumunda eşit olabilir. Aşağıdaki koşulları karşıladıkları, derleyici iki örneği aynı türde bir örnek değerlendirir:  
  
-   Aynı derlemede edildiklerine bağlıdır.  
  
-   Özellikleri, aynı çıkarsanan türleri, aynı ada sahip ve aynı sırada bildirilir. Adı karşılaştırmalar büyük küçük harfe duyarlı değildir.  
  
-   Her aynı özellikleri anahtar özellik olarak işaretlenir.  
  
-   Her bildiriminde en az bir özellik anahtar bir özelliktir.  
  
 Hiçbir anahtar özellikleri olan anonim bir tür örneği yalnızca kendisine eşittir.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Anonim türdeki iki örneği değerleri kendi anahtar özelliklerinin eşitse eşit olur. Aşağıdaki örnekler, eşitlik nasıl sınanır gösterir.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Salt okunur değerleri  
 Anahtar özelliklerin değerlerini değiştirilemez. Örneğin, `prod8` önceki örnekte, `Name` ve `Price` alanlar `read-only`, ancak `OnHand` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Sorgu ifadeleri anonim türleri  
 Sorgu ifadeleri, her zaman anonim türler oluşturulmasını gerektirmez. Mümkün olduğunda, bunlar mevcut türü sütun verileri tutmak için kullanın. Bu durum, sorgu, veri kaynağından veya her kaydın yalnızca bir alan ya da tüm kayıtları döndürür. oluşur. Aşağıdaki kod örnekleri, `customers` nesneleri koleksiyonudur bir `Customer` sınıfı. Sınıf çok sayıda özelliğe sahiptir ve herhangi bir sırada sorgu sonucundaki birini veya birkaçını içerebilir. İlk iki örneklerde sorgular adlandırılmış türler öğelerini seçin. çünkü hiçbir anonim türler gereklidir:  
  
-   `custs1` dizelerden oluşan bir koleksiyon olduğundan içeren `cust.Name` bir dizedir.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
-   `custs2` bir koleksiyonunu içerir `Customer` , çünkü nesnelerini her öğeye `customers` olduğu bir `Customer` nesne ve tüm öğeyi sorgu seçilmedi.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Ancak, uygun adlandırılmış türlerin her zaman kullanılabilir değildir. Müşteri adları ve adresleri bir amacı, müşteri kimlik numaraları ve başka konumları ve müşteri adları, adresleri ve siparişi geçmişi için üçüncü seçmek isteyebilirsiniz. Anonim türler sonucu tutmak için yeni bir adlandırılmış tür bildirmeden özellikleri, herhangi bir birleşimini herhangi bir sırada seçmenize olanak sağlar. Bunun yerine, derleyicinin özelliklerinin her derleme için anonim bir tür oluşturur. Aşağıdaki sorguda yalnızca müşterinin adı ve kimlik numarasını her birinden seçer `Customer` nesnesine `customers`. Bu nedenle, derleyici, bu iki özellik içeren bir anonim tür oluşturur.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Adları hem anonim tür özelliklerinde veri türlerini bağımsız değişkenleri alınmıştır `Select`, `cust.Name` ve `cust.ID`. Bir sorgu tarafından oluşturulan bir anonim tür özellikleri her zaman önemli özelliklerdir. Zaman `custs3` aşağıdaki yürütülür `For Each` döngü, sonucu olan iki anahtar özellikleri olan anonim bir türün örneklerinin bir koleksiyonunu `Name` ve `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Tarafından temsil edilen bir koleksiyondaki öğeleri `custs3` kesin olarak belirlenmiştir, kullanılabilir özellikler gidin ve bunların türlerini doğrulamak için IntelliSense'i kullanabilirsiniz.  
  
 Daha fazla bilgi için [Visual Basic'te LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Anonim türler kullanmak karar verme  
 Bir nesne anonim bir sınıf örneği oluşturmadan önce en iyi seçenek olup olmadığını göz önünde bulundurun. Örneğin, ilgili verileri içeren geçici bir nesne oluşturmak istediğiniz ve diğer alanlar ve tam sınıf içerebilecek yöntemler gerek varsa, anonim bir tür iyi bir çözümdür. Anonim türler, ayrıca her bildirimi için farklı bir özellik seçimi istiyorsanız veya özelliklerin sırasını değiştirmek istiyorsanız kullanışlıdır. Projenize bir sabit sırayla aynı özelliklere sahip birçok nesne varsa, ancak bunları daha kolay adlandırılmış tür ile bir sınıf oluşturucusunu kullanarak bildirebilirsiniz. Örneğin, uygun bir Oluşturucu ile çeşitli örneklerini bildirmek daha kolay olduğu bir `Product` anonim bir tür çeşitli örneklerini bildirmek için olandan sınıfı.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Adlandırılmış tür başka bir avantajı, derleyici bir özellik adı yanlışlıkla bir yanlış yazmanız catch ' dir. Önceki örneklerde, `firstProd2`, `secondProd2`, ve `thirdProd2` aynı anonim türdeki örneklerin olacak şekilde tasarlanmıştır. Ancak, yanlışlıkla alınmış bildirmek `thirdProd2` aşağıdaki yollardan birinde türünü sunucusundan farklı olacaktır `firstProd2` ve `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Daha da önemlisi, adlandırılmış türlerin örnekleri için geçerli olmayan anonim türlerin kullanılması ile ilgili sınırlamalar vardır. `firstProd2`, `secondProd2`, ve `thirdProd2` aynı anonim tür örnekleridir. Ancak, paylaşılan bir anonim tür adı yok ve bir tür adı kodunuzda beklenirken yer alamaz. Örneğin, anonim bir tür, başka bir değişken veya alanına ya da herhangi bir tür bildiriminde bildirmek için bir yöntem imzası tanımlamak için kullanılamaz. Anonim türler sonuç olarak, uygun değildir, bu yöntemler arasında bilgi paylaşımı sahip olduğunuzda.  
  
## <a name="an-anonymous-type-definition"></a>Bir anonim tür tanımı  
 Anonim bir türün bir örneği bildirimine yanıt olarak, derleyici belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.  
  
 Anonim tür en az bir anahtar özellik içeriyorsa, devralınan üç üye tanımı geçersiz kılar <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. Eşitlik sınamasını ve karma kodu değeri yalnızca anahtar özelliklerini göz önünde bulundurur belirlemek için kod üretti. Anonim tür hiçbir anahtar özellikler, yalnızca içerip içermediğini <xref:System.Object.ToString%2A> geçersiz kılınır. Anonim bir türün açıkça adlandırılmış özellikleri ile oluşturulan bu yöntemleri çakışamaz. Diğer bir deyişle, kullanamazsınız `.Equals`, `.GetHashCode`, veya `.ToString` adlı bir özelliği için.  
  
 En az bir içeren anonim tür tanımlarını anahtar özellik de uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi, burada `T` anonim tür türüdür.  
  
 Derleyici ve işlevlerini geçersiz kılınan yöntemler tarafından oluşturulan kodu hakkında daha fazla bilgi için bkz. [anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Anonim Tip Tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
