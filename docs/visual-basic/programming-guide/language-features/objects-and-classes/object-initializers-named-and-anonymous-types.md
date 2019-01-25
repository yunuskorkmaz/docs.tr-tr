---
title: 'Nesne başlatıcıları: Adlandırılmış ve anonim türler (Visual Basic)'
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
ms.openlocfilehash: f65352ebd9ca12aaed6b469c5df136301e9f839c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620545"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Nesne başlatıcıları: Adlandırılmış ve anonim türler (Visual Basic)
Nesne başlatıcıları, tek bir ifade kullanarak karmaşık bir nesnenin özelliklerini belirtmek etkinleştirin. Örnekleri adlandırılmış türler ve anonim türler oluşturmak için kullanılabilir.  
  
## <a name="declarations"></a>Bildirimler  
 Adlandırılmış ve anonim türlerin örneklerini bildirimlerini neredeyse aynı görünebilir, ancak etkilerini aynı değildir. Her kategorinin yeteneklerini ve kendi kısıtlamaları vardır. Aşağıdaki örnek, bildirmek ve adlandırılmış bir sınıf örneği başlatmak için kullanışlı bir yol gösterir. `Customer`, nesne başlatıcı listesi kullanılarak. Sınıfın adı anahtar sözcüğü sonra belirtildiğine dikkat edin `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Anonim bir tür kullanılabilir adı yok. Bu nedenle örneklemesi anonim bir türün bir sınıf adı içeremez.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Gereksinimler ve iki bildirimi sonuçlarını aynı değildir. İçin `namedCust`, `Customer` sahip sınıf bir `Name` özelliği zaten var olmalıdır ve bu sınıfın bir örneğini bildirimi oluşturur. İçin `anonymousCust`, derleyici bir özelliği, bir dize olarak adlandırılan yeni bir sınıf tanımlar `Name`ve bu sınıfın yeni bir örneğini oluşturur.  
  
## <a name="named-types"></a>Adlandırılmış türler  
 Nesne başlatıcıları, bir türü oluşturucusunu çağırın ve ardından tek bir deyimde bazı veya tüm özelliklerin değerlerini ayarlamak için basit bir yol sağlar. Derleyici deyimi için uygun oluşturucuyu çağırır: varsayılan oluşturucu bağımsız değişken olmadan sunulursa ya da bir veya daha fazla bağımsız değişken gönderiliyorsa parametreli bir oluşturucu. Bundan sonra belirtilen özellikleri Başlatıcı listesinde görüntülenen sırayla başlatılır.  
  
 Sınıf üyesi için bir başlangıç değeri atamasının Başlatıcı listesinde her başlatma oluşur. Sınıf tanımlandığı zaman adları ve veri türleri ve üyeleri belirlenir. Aşağıdaki örneklerde, `Customer` sınıfı var olmalıdır ve üyeleri adlı sahip `Name` ve `City` dize değerlerini kabul edebilir.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Her biri bu bildirimleri oluşturur aşağıdaki örneğe eşdeğerdir bir `Customer` nesnesinin varsayılan Oluşturucusu kullanarak ve ardından başlangıç değerlerini belirten `Name` ve `City` özellikleri kullanılarak bir `With` deyimi.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Varsa `Customer` parametreli bir kurucu için bir değer göndermenizi sağlar sınıfını içeren `Name`, örneğin, aynı zamanda bildirmek başlatmak ve bir `Customer` nesneyi aşağıdaki yollarla:  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Tüm özellikleri, aşağıdaki kodun gösterdiği olarak başlatmak zorunda değildir.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 Ancak, başlatma listesi boş olamaz. Başlatılmamış özelliklere varsayılan değerlerini korur.  
  
### <a name="type-inference-with-named-types"></a>Adlandırılmış türler ile tür çıkarımı  
 Kod bildirimi için kısaltabilir `cust1` nesne başlatıcıları ve yerel tür çıkarımı birleştirerek. Bu sayede atlamak `As` yan tümcesinde değişken bildirimi. Değişkenin veri türü ataması tarafından oluşturulan nesnenin türü gösterilir. Aşağıdaki örnekte, türü `cust6` olduğu `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Adlandırılmış türler hakkında açıklamalar  
  
-   Sınıf üyesi nesne Başlatıcı listesinde birden fazla kez başlatılamaz. Bildirimi `cust7` bir hataya neden olur.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Üye, kendisiyle veya başka bir alanı başlatmak için kullanılabilir. Bunu, aşağıdaki bildirimi için olduğu gibi başlatılmadan önce üye erişiliyorsa `cust8`, varsayılan değer kullanılır. Nesne Başlatıcı kullanan bir bildirim işlendiğinde gerçekleşen ilk şey uygun Oluşturucu çağrılır olduğunu unutmayın. Bundan sonra tek tek alanları Başlatıcı listesinde başlatılır. Aşağıdaki örneklerde, varsayılan değer için `Name` atanmış `cust8`, başlatılmış bir değer atanır `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     Aşağıdaki örnek, parametreli oluşturucudan kullanır `cust3` ve `cust4` bildirmek ve başlatmak için `cust10` ve `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Nesne başlatıcıları yuvalanabilir. Aşağıdaki örnekte, `AddressClass` iki özelliklere sahip bir sınıf olan `City` ve `State`ve `Customer` sınıfında bir `Address` örneğidir özelliği `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   Başlatma listesi boş olamaz.  
  
-   Başlatılmakta örneği nesne türünde olamaz.  
  
-   Paylaşılan üyeleri, salt okunur üyeler, sabitler veya yöntem çağrılarını başlatılmakta sınıf üyeleri olamaz.  
  
-   Sınıf üyeleri başlatılmakta dizine veya uygun. Aşağıdaki örnekler, derleyici hataları Yükselt:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler değil açıkça tanımladığınız yeni türler ve ad örnekleri oluşturmak için nesne başlatıcıları kullanın. Bunun yerine derleyici sizin belirlediğiniz özelliklerine göre bir tür nesne Başlatıcı listesinde oluşturur. Türünün adı belirtilmediğinden bu şeklinde adlandırılan bir *anonim tür*. Örneğin, aşağıdaki bildirimi için önceki bir karşılaştırma `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 Tek fark, sözdizimsel olarak sonra adı belirtilmezse, `New` veri türü. Ancak, oldukça farklı olur. Derleyici iki özelliklere sahip yeni bir anonim tür tanımlar `Name` ve `City`, belirtilen değerlerle bir örneğini oluşturur. Tür çıkarımı türlerini belirler `Name` ve `City` dizeler için örnekte.  
  
> [!CAUTION]
>  Anonim tür adı derleyici tarafından oluşturulan ve derleme başka bir derleme farklılık gösterebilir. Kodunuzu kullanın veya anonim bir türün adına dayanan gerekir.  
  
 Kullanamazsınız, türünün adı kullanılamaz çünkü bir `As` bildirmek için yan tümcesi `cust13`. Kendi türün gösterilmesi gerekir. Geç bağlama kullanmadan, bu yerel değişkenlere anonim türler kullanımını sınırlar.  
  
 Anonim türler sağlamak için destek gerektiren kritik [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular. Anonim türler sorgularda kullanımı hakkında daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [Visual Basic'te LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Anonim türler hakkında açıklamalar  
  
-   Genellikle, tüm veya çoğu bir anonim tür bildirimi özelliklerinde anahtar sözcüğü yazarak belirtilen anahtar özellikleri olacaktır `Key` önünde özellik adı.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Anahtar özellikleri hakkında daha fazla bilgi için bkz. [anahtar](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Anonim tür tanımlarını en az bir özellik bildirmelidir için türler, başlatıcı listeleri gibi adı.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Anonim bir türün bir örneği bildirildiğinde, derleyici eşleşen bir anonim tür tanımı oluşturur. Adları ve veri türleri özelliklerinin örneği bildirimden alınır ve tanımındaki derleyici tarafından yer alır. Özellikler yok adlı ve bunlar için adlandırılmış bir tür olduğu gibi önceden tanımlanmış. Türlerini algılanır. Veri türlerini özelliklerini kullanarak belirtemezsiniz bir `As` yan tümcesi.  
  
-   Anonim türler de adlarını ve bunların özelliklerinin değerlerini diğer çeşitli yollarla oluşturabilirsiniz. Örneğin, bir anonim tür özelliği hem adı hem de bir değişken veya adı değerini ve başka bir nesnenin bir özelliğini değerini alabilir.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Anonim türleri özellikleri tanımlamaya yönelik seçenekler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
