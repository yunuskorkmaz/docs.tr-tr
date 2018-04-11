---
title: Anonim Türleri (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 530e21e1595f9bbc3436280418287413e2a48111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-types-visual-basic"></a>Anonim Türleri (Visual Basic)
Visual Basic veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmanıza olanak sağlaması anonim türler destekler. Bunun yerine, derleyici bir sınıf sizin için oluşturur. Sınıf kullanılabilir bir ada sahip değil, doğrudan öğesinden devralınan <xref:System.Object>ve nesne bildirme belirttiğiniz özellikler içerir. Veri türünün adı belirtilmediğinden, bu olarak adlandırılır bir *anonim tür*.  
  
 Aşağıdaki örnek bildirir ve değişken oluşturur `product` iki özelliklere sahip anonim bir türün bir örneği olarak `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 A *sorgu ifadesi* bir sorgu tarafından seçilen veri sütunlarının birleştirmek için anonim tür kullanır. Belirli bir sorgu seçebilirsiniz sütunları tahmin etmek için sonuç türü önceden tanımlayamazsınız. Anonim türler herhangi bir sırada sütunları, herhangi bir sayıda seçen bir sorgu yazmak etkinleştirin. Derleyici belirtilen özelliklere ve belirtilen sırayla eşleşen bir veri türü oluşturur.  
  
 Aşağıdaki örneklerde, `products` ürün nesneleri, her birinin olan birçok özellik listesini içerir. Değişken `namePriceQuery` yürütüldüğünde, iki özelliklere sahip anonim bir türün örneklerinin bir koleksiyonunu döndüren bir sorgu tanımını tutan `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 Değişken `nameQuantityQuery` yürütüldüğünde, iki özelliklere sahip anonim bir türün örneklerinin bir koleksiyonunu döndüren bir sorgu tanımını tutan `Name` ve `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 Anonim bir tür için derleyici tarafından oluşturulan kodu hakkında daha fazla bilgi için bkz: [anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Derleyici oluşturulur ve derleme derleme değişebilir anonim tür adıdır. Kodunuzu kullanın veya bir Proje derlenir zaman adı değişebileceğinden anonim bir tür adına bağlı gerekir.  
  
## <a name="declaring-an-anonymous-type"></a>Anonim bir tür bildirme  
 Anonim bir türün bir örneği bildirimi başlatıcı listesi türünün özelliklerini belirtmek için kullanır. Anonim bir tür, değil yöntemleri ya da olaylar gibi diğer sınıfı öğelerini bildirdiğiniz seçtiğinizde yalnızca özellikleri belirtebilirsiniz. Aşağıdaki örnekte, `product1` iki özelliklere sahip anonim bir türün bir örneği: `Name` ve `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 Özellikleri anahtar özellik olarak belirlerseniz, iki anonim tür örneği eşitlik karşılaştırmak için kullanabilirsiniz. Ancak, anahtar özellik değerleri değiştirilemez. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde anahtar özellikleri bölümüne bakın.  
  
 Anonim bir türün bir örneği bildirme nesne Başlatıcı kullanarak adlandırılmış bir türün bir örneği bildirme gibi olduğuna dikkat edin:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 Anonim tür özelliklerini belirtmek için diğer yolları hakkında daha fazla bilgi için bkz: [nasıl yapılır: Infer özellik adları ve türlerini anonim türde bildirimlerden](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özellikler anahtar olmayan özelliklerinden bazı temel farklar:  
  
-   İki örneği eşit olup olmadığını belirlemek için yalnızca anahtar özellikler değerlerini karşılaştırılır.  
  
-   Anahtar özellik değerlerini salt okunurdur ve değiştirilemez.  
  
-   Yalnızca anahtar özellik değerlerini derleyici tarafından üretilen karma kodu algoritması anonim bir tür için dahil edilmiştir.  
  
### <a name="equality"></a>Eşitlik  
 Anonim türler örnekleri aynı anonim türdeki örneklerin yalnızca olmaları durumunda eşit olabilir. Aşağıdaki koşullar karşılıyorsa derleyici iki örneği aynı türde bir örnekleri olarak kabul eder:  
  
-   Bunlar aynı bütünleştirilmiş kodda bildirilir.  
  
-   Özellikleri aynı oluşturulursa türleri, aynı ada sahip ve aynı sırada bildirilir. Adı karşılaştırmaları büyük küçük harfe duyarlı değildir.  
  
-   Her aynı özellikleri anahtar özellik olarak işaretlenir.  
  
-   Her bildiriminde en az bir özellik anahtar bir özelliktir.  
  
 Hiçbir anahtar özellikleri olan anonim türler örneği yalnızca kendisine eşittir.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 İki aynı anonim tür anahtar özelliklerini değerleri aynıysa eşit örnekleridir. Aşağıdaki örneklerde eşitlik nasıl test gösterilmektedir.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a>Salt okunur değerleri  
 Anahtar özellikleri değerleri değiştirilemez. Örneğin, `prod8` önceki örnekte, `Name` ve `Price` alanlar `read-only`, ancak `OnHand` değiştirilebilir.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Sorgu ifadeleri anonim türler  
 Sorgu ifadeleri anonim türler oluşturulmasını her zaman gerektirmez. Mümkün olduğunda, mevcut bir türle sütun veri tutmak için kullanırlar. Bu durum, veri kaynağına veya her kaydından tek alanından ya da tüm kayıtları sorgunun döndürdüğü oluşur. Aşağıdaki kod örnekleri, `customers` nesneleri koleksiyonudur bir `Customer` sınıfı. Pek çok özellik sınıfı vardır ve herhangi bir sırada sorgu sonucunda bir veya daha fazlası içerebilir. İlk iki örneklerde, sorguları adlandırılmış türler öğeleri belirlediğiniz için anonim tür gereklidir:  
  
-   `custs1`dizeleri koleksiyonu çünkü içeriyor `cust.Name` bir dizedir.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2`bir koleksiyonu içerir `Customer` , çünkü nesnelerini her öğeye `customers` olan bir `Customer` nesne ve tüm öğesi sorgu tarafından seçilen.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 Ancak, uygun adlandırılmış türler her zaman kullanılabilir değildir. Müşteri adları ve bir amacı, Müşteri Kimliği numaraları ve başka konumları için adresleri, üçüncü bir siparişi geçmişi ve müşteri adları ve adresleri seçmek isteyebilirsiniz. Anonim türler sonucu tutmak için yeni bir adlandırılmış türü bildirmeden herhangi bir sırada özellikleri, herhangi bir bileşimini seçmenizi sağlar. Bunun yerine, derleyici özelliklerinin her derleme için anonim bir tür oluşturur. Aşağıdaki sorguda yalnızca müşterinin adını ve kimlik numarasını her birinden seçer `Customer` nesnesinde `customers`. Bu nedenle, derleyici, bu iki özellik içeren bir anonim türü oluşturur.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 Bağımsız değişkenler için gelen adlarını ve anonim tür özelliklerinde veri türlerini gerçekleştirilecek `Select`, `cust.Name` ve `cust.ID`. Bir sorgu tarafından oluşturulan anonim bir tür özelliklerinde her zaman anahtar özelliklerdir. Zaman `custs3` aşağıdakileri yürütülen `For Each` döngü, sonucu olan iki anahtar özelliklere sahip anonim bir türün örneklerinin bir koleksiyonunu `Name` ve `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 Tarafından temsil edilen koleksiyondaki öğelerin `custs3` kesin türü belirtilmiş ve IntelliSense kullanılabilir özellikler gidin ve bunların türlerine doğrulamak için kullanabilirsiniz.  
  
 Daha fazla bilgi için bkz: [Visual Basic'te LINQ giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Anonim türler kullanmaya karar verme  
 Anonim bir sınıfın bir örneği nesneyi oluşturmadan önce en iyi seçenek olup olmadığını belirleyin. Örneğin, ilgili verileri içeren geçici bir nesne oluşturmak istediğiniz ve diğer alan ve tam bir sınıf içerebilir yöntemleri gerek varsa, anonim bir tür iyi bir çözümdür. Anonim türler, ayrıca her bildirim için farklı bir seçim özelliklerinin istiyorsanız veya özelliklerin sırasını değiştirmek istiyorsanız kullanışlıdır. Projenizi sabit bir sırada aynı özelliklere sahip birçok nesne varsa, ancak bunları daha kolay bir sınıf oluşturucu adlandırılmış türü kullanarak bildirebilirsiniz. Örneğin, uygun bir Oluşturucu ile çeşitli örneklerine bildirmek kolay bir `Product` anonim bir tür çeşitli örneklerine bildirmektir değerinden sınıf.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 Adlandırılmış türler başka bir avantajı, bir özellik adı yanlışlıkla bir yanlış yazmanız derleyici yakalayabilir ' dir. Önceki örneklerde, `firstProd2`, `secondProd2`, ve `thirdProd2` aynı anonim türdeki örneklerin olacak şekilde tasarlanmıştır. Ancak, yanlışlıkla gerçekleştirilen bildirme `thirdProd2` aşağıdaki yollardan birinde türünü değerinden farklı olacaktır `firstProd2` ve `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 Daha da önemlisi, adlandırılmış türler örneklerine uygulamayın anonim türler kullanma sınırlamaları vardır. `firstProd2`, `secondProd2`, ve `thirdProd2` aynı anonim tür örnekleridir. Ancak, paylaşılan anonim türü için bir ad kullanılamaz ve tür adı kodunuzda beklenirken yer alamaz. Örneğin, anonim bir tür başka bir değişken veya alan ya da tüm türü bildiriminde bildirmek için bir yöntem imzası tanımlamak için kullanılamaz. Anonim türler sonuç olarak, uygun değildir, bu yöntemleri arasında bilgi paylaşımı sahip olduğunuzda.  
  
## <a name="an-anonymous-type-definition"></a>Anonim tür tanımı  
 Anonim bir türün bir örneği bildirimine yanıt olarak, belirtilen özellikleri içeren yeni bir sınıf tanımı derleyici oluşturur.  
  
 Anonim tür en az bir anahtar özellik içeriyorsa, tanım devralınan üç üyeleri geçersiz kılar <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>. Kod üretti. eşitlik sınamasını ve yalnızca anahtar özellikler karma kodu değerini dikkate belirlemek için. Anonim tür anahtar özellik, yalnızca içeriyorsa <xref:System.Object.ToString%2A> geçersiz kılınır. Anonim bir türün açıkça adlandırılmış özellikleri oluşturulan bu yöntemlerle çakışmamalıdır. Diğer bir deyişle, kullanamazsınız `.Equals`, `.GetHashCode`, veya `.ToString` bir özellik adı için.  
  
 En az bir tane anonim tür tanımları anahtar özelliği de uygulama <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi, burada `T` anonim tür türüdür.  
  
 Derleyici ve geçersiz kılınan yöntemleri işlevselliğini tarafından oluşturulan kodu hakkında daha fazla bilgi için bkz: [anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Nasıl yapılır: özellik adları ve türlerini anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Anonim tür tanımı](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Anahtarı](../../../../visual-basic/language-reference/modifiers/key.md)
