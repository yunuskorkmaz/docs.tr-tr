---
title: 'Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler'
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
ms.openlocfilehash: e6ffc649d7eb841c2d009b0ec1237975f46e2d2d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636815"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler (Visual Basic)
Nesne başlatıcıları, tek bir ifade kullanarak karmaşık bir nesne için özellikler belirtmenize olanak tanır. Bunlar, adlandırılmış türlerin örnekleri ve anonim türler oluşturmak için kullanılabilir.  
  
## <a name="declarations"></a>Bildirimler  
 Adlandırılmış ve anonim türdeki örneklerin bildirimleri neredeyse özdeş olabilir, ancak etkileri aynı değildir. Her kategori kendi yeteneklerini ve kısıtlamalarını içerir. Aşağıdaki örnek, bir nesne Başlatıcısı listesi kullanarak `Customer`adlandırılmış bir sınıfın örneğini bildirmek ve başlatmak için kullanışlı bir yol gösterir. Sınıf adının `New`anahtar sözcüğünden sonra belirtildiğine dikkat edin.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Anonim bir türün kullanılabilir adı yok. Bu nedenle, anonim bir türün örneklemesi bir sınıf adı içeremez.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 İki bildirime ait gereksinimler ve sonuçlar aynı değildir. `namedCust`için, bir `Name` özelliğine sahip bir `Customer` sınıfı zaten var olmalıdır ve bildirim bu sınıfın bir örneğini oluşturur. `anonymousCust`, derleyici bir özelliği olan yeni bir sınıf tanımlar, `Name`adlı bir dize ve bu sınıfın yeni bir örneğini oluşturur.  
  
## <a name="named-types"></a>Adlandırılmış türler  
 Nesne başlatıcıları, bir türün yapıcısını çağırmak için basit bir yol sağlar ve sonra bazı veya tüm özelliklerin değerlerini tek bir deyime göre ayarlar. Derleyici, bir veya daha fazla bağımsız değişken gönderildiyse parametresiz Oluşturucu veya bir veya daha fazla bağımsız değişken gönderilirse parametreli Oluşturucu olarak ifade için uygun oluşturucuyu çağırır. Bundan sonra, belirtilen özellikler Başlatıcı listesinde sunuldukları sırada başlatılır.  
  
 Başlatıcı listesindeki her başlatma, sınıfın bir üyesine ilk değer atamasından oluşur. Üyelerin adları ve veri türleri, sınıf tanımlandığında belirlenir. Aşağıdaki örneklerde `Customer` sınıfı var olmalıdır ve dize değerlerini kabul edebilecek `Name` ve `City` adlı üyelere sahip olmalıdır.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Bu bildirimlerin her biri, parametresiz oluşturucuyu kullanarak bir `Customer` nesnesi oluşturan aşağıdaki örneğe eşdeğerdir ve sonra `Name` ve `City` özellikler için ilk değerleri `With` bir ifade kullanarak belirtir.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 `Customer` sınıfı, `Name`için bir değer göndermenizi sağlayan parametreli bir Oluşturucu içeriyorsa, örneğin, aşağıdaki yollarla bir `Customer` nesnesi bildirip de başlatabilirsiniz:  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Aşağıdaki kodda gösterildiği gibi tüm özellikleri başlatmak zorunda değilsiniz.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Ancak, başlatma listesi boş olamaz. Başlatılmamış özellikler varsayılan değerlerini korurlar.  
  
### <a name="type-inference-with-named-types"></a>Adlandırılmış türlerle tür çıkarımı  
 Nesne başlatıcıları ve yerel tür çıkarımı birleştirerek `cust1` bildirimi için kodu kısaltabilirsiniz. Bu, değişken bildiriminde `As` yan tümcesini atlamanızı sağlar. Değişkenin veri türü, atama tarafından oluşturulan nesnenin türünden algılanır. Aşağıdaki örnekte `cust6` türü `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Adlandırılmış türler hakkında açıklamalar  
  
- Bir sınıf üyesi, nesne başlatıcısı listesinde birden çok kez başlatılamaz. `cust7` bildirimi hataya neden olur.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- Bir üye, kendisini veya başka bir alanı başlatmak için kullanılabilir. Bir üyeye başlatıldıktan sonra, `cust8`için aşağıdaki bildirimde olduğu gibi, varsayılan değer kullanılacaktır. Bir nesne Başlatıcısı kullanan bir bildirim işlendiğinde, gerçekleşen ilk şey uygun oluşturucunun çağrılmakta olduğunu unutmayın. Bundan sonra, Başlatıcı listesindeki ayrı alanlar başlatılır. Aşağıdaki örneklerde `Name` için varsayılan değer `cust8`atanır ve başlatılmış bir değer `cust9`atanır.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     Aşağıdaki örnek, `cust10` ve `cust11`bildirmek ve başlatmak için `cust3` ve `cust4` parametreli oluşturucuyu kullanır.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Nesne başlatıcıları iç içe olabilir. Aşağıdaki örnekte `AddressClass`, `City` ve `State`iki özelliği olan bir sınıftır ve `Customer` sınıfı `Address` örneği olan bir `AddressClass`özelliğine sahiptir.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- Başlatma listesi boş olamaz.  
  
- Başlatılan örnek Object türünde olamaz.  
  
- Başlatılan sınıf üyeleri, paylaşılan Üyeler, salt okuma üyeleri, sabitler veya yöntem çağrıları olamaz.  
  
- Başlatılan sınıf üyeleri dizinlenemez veya nitelenmiyor. Aşağıdaki örnekler derleyici hatalarını yükseltir:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler, açıkça tanımlamadığınız ve isimsiz olmayan yeni türlerin örneklerini oluşturmak için nesne başlatıcıları kullanır. Bunun yerine, derleyici, nesne başlatıcısı listesinde belirleyeceğiniz özelliklere göre bir tür üretir. Türün adı belirtilmediğinden, *anonim bir tür*olarak adlandırılır. Örneğin, aşağıdaki bildirimi `cust6`için önceki bir ile karşılaştırın.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Tek fark sözdizimi, veri türü için `New` sonrasında hiçbir adın belirtilme türüdür. Ancak, ne olur oldukça farklıdır. Derleyici, `Name` ve `City`iki özelliği olan yeni bir anonim tür tanımlar ve belirtilen değerlerle bunun bir örneğini oluşturur. Tür çıkarımı, dizeler gibi örnekteki `Name` ve `City` türlerini belirler.  
  
> [!CAUTION]
> Anonim türün adı derleyici tarafından oluşturulur ve derlemeden derlemeye değişiklik gösterebilir. Kodunuz, anonim bir türün adını kullanmamalıdır veya bu adı kullanmalıdır.  
  
 Türün adı kullanılamadığından, `cust13`bildirmek için bir `As` yan tümcesi kullanamazsınız. Türü çıkarsanmalıdır. Bu, geç bağlama kullanılmadan, anonim türlerin kullanımını yerel değişkenlere kısıtlar.  
  
 Anonim türler, LINQ sorguları için kritik destek sağlar. Sorgularda anonim türlerin kullanımı hakkında daha fazla bilgi için, bkz. Visual Basic [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [lınq 'ye giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Anonim türler hakkında açıklamalar  
  
- Genellikle, anonim bir tür bildirimindeki özelliklerin tümü veya çoğu, özellik adının önüne `Key` anahtar sözcüğü yazılarak belirtilen temel özelliklerdir.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Anahtar özellikleri hakkında daha fazla bilgi için bkz. [anahtar](../../../../visual-basic/language-reference/modifiers/key.md).  
  
- Adlandırılmış türler gibi, anonim tür tanımlarının başlatıcı listeleri en az bir özellik bildirmelidir.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- Anonim türün bir örneği bildirildiğinde, derleyici eşleşen bir anonim tür tanımı oluşturur. Özelliklerin adları ve veri türleri örnek bildiriminden alınır ve tanımda derleyici tarafından dahil edilir. Adlandırılmış bir tür için olduklarından özellikler önceden adlandırılmaz ve önceden tanımlanmamıştır. Türleri algılanır. `As` yan tümcesini kullanarak özelliklerin veri türlerini belirtemezsiniz.  
  
- Anonim türler, özelliklerinin adlarını ve değerlerini birkaç farklı yolla de kurabilir. Örneğin, anonim bir tür özelliği bir değişkenin adını ve değerini ya da başka bir nesnenin özelliğinin adını ve değerini alabilir.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Anonim türlerde özellikleri tanımlamaya yönelik seçenekler hakkında daha fazla bilgi için bkz. [nasıl yapılır: özellik adlarını ve türleri anonim tür bildirimlerinde çıkarım](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
