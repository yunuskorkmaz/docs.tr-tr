---
title: 'Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 612b1dcea0f776dfd4580803e76f2785e7d28da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)
Nesne başlatıcılar, tek bir ifade kullanarak karmaşık bir nesne özelliklerini belirtmenize olanak verir. Adlandırılmış türler ve anonim türler örnekleri oluşturmak için kullanılabilir.  
  
## <a name="declarations"></a>Bildirimler  
 Adlandırılmış ve anonim türler örneklerinin bildirimleri neredeyse aynı görünebilir, ancak etkilerini aynı değildir. Her kategori yeteneklerini ve kendi kısıtlamaları vardır. Aşağıdaki örnek, bildirme ve bir adlandırılmış sınıfının bir örneği başlatmak için kolay bir yol gösterir `Customer`, bir nesne Başlatıcı listesini kullanarak. Sınıfın adını anahtar sözcüğü sonra belirttiğiniz fark `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Anonim bir tür kullanılabilir adı yok. Bu nedenle bir örnek oluşturma anonim bir türün bir sınıf adı içeremez.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Gereksinimler ve iki bildirimleri sonuçlarını aynı değildir. İçin `namedCust`, `Customer` olan sınıfı bir `Name` özellik zaten var olmalıdır ve bildirimi o sınıfın bir örneğini oluşturur. İçin `anonymousCust`, derleyici bir özelliği, bir dize olarak adlandırılan yeni bir sınıf tanımlar `Name`ve o sınıfın yeni bir örneğini oluşturur.  
  
## <a name="named-types"></a>Adlandırılmış türler  
 Nesne başlatıcıları türü kurucusunu çağırmak ve ardından tek bir deyimde bazı veya tüm özelliklerinin değerlerini ayarlamak için basit bir yol sağlar. Deyim uygun Oluşturucusu derleyici çağırır: bağımsız değişken içermeyen görüntülenirse varsayılan oluşturucu veya bağımsız değişkenlerden biri veya daha fazla gönderilirse parametreli bir oluşturucu. Başlatıcı listesinde verildikleri sırada bundan sonra belirtilen özellikleri başlatılır.  
  
 Sınıf üyesi için bir başlangıç değeri atamasının Başlatıcı listesindeki her başlatma oluşur. Sınıf tanımladığınızda adları ve veri türleri üyeleri belirlenir. Aşağıdaki örneklerde, `Customer` sınıfı bulunması gerektiğini ve üyeleri adlı sahip `Name` ve `City` dize değerlerini kabul edebilir.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Bu bildirimler her oluşturur aşağıdaki örneğe eşdeğerdir bir `Customer` nesnesi varsayılan oluşturucu kullanılarak ve sonra Başlangıç değerlerini belirtir `Name` ve `City` özelliklerini kullanarak bir `With` deyimi.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Varsa `Customer` sınıfı için bir değer göndermenize olanak sağlayan bir parametreli oluşturucu içeren `Name`, örneğin, aynı zamanda bildirme başlatmak ve bir `Customer` aşağıdaki yollarla nesnesi:  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Aşağıdaki kod gösterildiği gibi tüm özellikleri başlatma gerekmez.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 Ancak, başlatma listesi boş olamaz. Başlatılmamış özellikler varsayılan değerleri korur.  
  
### <a name="type-inference-with-named-types"></a>Adlandırılmış türleriyle tür çıkarımı  
 Bildirimi için kod kısaltabilir `cust1` nesne başlatıcıları ve yerel türü çıkarımı birleştirerek. Bu, atlamanızı sağlar `As` yan tümcesinde değişken bildirimi. Değişken veri türü atama tarafından oluşturulan nesnenin türünden algılanır. Aşağıdaki örnekte, türü `cust6` olan `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Adlandırılmış türler hakkında açıklamalar  
  
-   Sınıf üyesine nesne Başlatıcı listesinde birden fazla kez başlatılamaz. Bildirimi `cust7` bir hataya neden olur.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Üye kendisiyle veya başka bir alanı başlatmak için kullanılabilir. Bunu, aşağıdaki gibi başlatılmadan önce üyesi erişiliyorsa `cust8`, varsayılan değer kullanılır. Nesne Başlatıcı kullanan bir bildirimi işlendiğinde olur ilk şey uygun Oluşturucusu çağrılır olduğunu unutmayın. Bundan sonra tek tek alanların Başlatıcı listesinde başlatılır. Aşağıdaki örneklerde, varsayılan değer için `Name` için atanan `cust8`, ve başlatılmış bir değeri atandığı `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     Aşağıdaki örnek, parametreli oluşturucudan kullanır `cust3` ve `cust4` bildirme ve başlatmak için `cust10` ve `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Nesne başlatıcıları iç içe. Aşağıdaki örnekte, `AddressClass` iki özelliğe sahip bir sınıf `City` ve `State`ve `Customer` sınıfına sahip bir `Address` örneği özelliği `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   Başlatma listesi boş olamaz.  
  
-   Başlatılmakta örnek nesne türünde olamaz.  
  
-   Sınıf üyeleri başlatılmakta paylaşılan üyeler, salt okunur üyeler, sabitleri ve yöntem çağrılarını olamaz.  
  
-   Sınıf üyeleri başlatılmakta dizine veya tam. Aşağıdaki örnekler derleyici hataları Yükselt:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler nesne başlatıcıları değil açıkça tanımladığınız yeni türler ve ad örnekleri oluşturmak için kullanın. Bunun yerine, derleyici nesne Başlatıcı listesinde belirttiğiniz özellikler göre bir türü oluşturur. Türünün adı belirtilmediğinden, bu olarak adlandırılır bir *anonim tür*. Örneğin, aşağıdaki bildirimi için önceki bir karşılaştırma `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 Yalnızca sözdizimsel olarak ad sonra belirttiğiniz farktır `New` veri türü için. Ancak, oldukça farklı olur. İki özelliklere sahip yeni bir anonim tür derleyici tanımlar `Name` ve `City`ve belirtilen değerlerle bir örneğini oluşturur. Tür çıkarımı belirler türlerini `Name` ve `City` dizeleri olması için örnekte.  
  
> [!CAUTION]
>  Anonim tür adını derleyici tarafından üretilen ve derleme derleme farklılık gösterebilir. Kodunuzu kullanın veya anonim bir tür adına bağlı gerekir.  
  
 Ad türü kullanılabilir olmadığından kullanamazsınız bir `As` bildirmek için yan tümcesi `cust13`. Tür çıkarımı yapılan gerekir. Geç bağlama kullanmadan bu anonim türleri yerel değişkenler için kullanımını kısıtlar.  
  
 Anonim türler için kritik destek sağlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular. Anonim türler sorgularda kullanımı hakkında daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [Visual Basic'te LINQ giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Anonim türler hakkında açıklamalar  
  
-   Genellikle, tüm veya anonim tür bildirimi özelliklerinin çoğu anahtar sözcüğü yazarak belirtilen anahtar özellikleri olur `Key` önünde özellik adı.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Anahtar özellikler hakkında daha fazla bilgi için bkz: [anahtar](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Anonim tür tanımları en az bir özellik bildirmelidir için türleri, başlatıcı listeleri gibi adlı.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Anonim bir türün bir örneği bildirilmişse derleyici eşleşen anonim tür tanımı oluşturur. Adları ve özellikler veri türlerinde örneği bildiriminden alınır ve tanımında derleyici tarafından dahil edilir. Özellikler yok adlı ve adlandırılmış türü için olduğu gibi önceden tanımlı. Bunların türlerine algılanır. Özellikler veri türlerini kullanarak belirtemezsiniz bir `As` yan tümcesi.  
  
-   Anonim türler ayrıca diğer çeşitli yollarla adlarını ve bunların özelliklerinin değerlerini kurabilirsiniz. Örneğin, anonim tür özellik hem adı hem de değeri bir değişken veya ad ve başka bir nesnenin bir özelliğini değerini alabilir.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Anonim türleri özelliklerini tanımlamak için seçenekleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: Infer özellik adları ve türlerini anonim türde bildirimlerden](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)  
 [Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
