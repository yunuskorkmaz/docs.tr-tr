---
title: 'Nesne Başlatıcıları: Adlandırılmış ve anonim türler (Visual Basic)'
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
ms.openlocfilehash: e1f461cc98fb104f78a6c83a207cff7f4eda9227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046457"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Nesne Başlatıcıları: Adlandırılmış ve anonim türler (Visual Basic)
Nesne başlatıcıları, tek bir ifade kullanarak karmaşık bir nesne için özellikler belirtmenize olanak tanır. Bunlar, adlandırılmış türlerin örnekleri ve anonim türler oluşturmak için kullanılabilir.  
  
## <a name="declarations"></a>Bildirimler  
 Adlandırılmış ve anonim türdeki örneklerin bildirimleri neredeyse özdeş olabilir, ancak etkileri aynı değildir. Her kategori kendi yeteneklerini ve kısıtlamalarını içerir. Aşağıdaki örnek, bir nesne Başlatıcısı listesi kullanarak, adlandırılmış bir sınıfın `Customer`bir örneğini bildirmek ve başlatmak için kullanışlı bir yol gösterir. Sınıfın adının anahtar sözcüğünden `New`sonra belirtildiğine dikkat edin.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Anonim bir türün kullanılabilir adı yok. Bu nedenle, anonim bir türün örneklemesi bir sınıf adı içeremez.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 İki bildirime ait gereksinimler ve sonuçlar aynı değildir. İçin `namedCust` ,özelliği`Name` olan bir sınıfzatenvarolmalıdırvebildirimbusınıfınbirörneğinioluşturur.`Customer` İçin `anonymousCust`, derleyici bir özelliğine sahip olan ve bir dize adlı `Name`yeni bir sınıf tanımlar ve bu sınıfın yeni bir örneğini oluşturur.  
  
## <a name="named-types"></a>Adlandırılmış türler  
 Nesne başlatıcıları, bir türün yapıcısını çağırmak için basit bir yol sağlar ve sonra bazı veya tüm özelliklerin değerlerini tek bir deyime göre ayarlar. Derleyici, bir veya daha fazla bağımsız değişken gönderildiyse parametresiz Oluşturucu veya bir veya daha fazla bağımsız değişken gönderilirse parametreli Oluşturucu olarak ifade için uygun oluşturucuyu çağırır. Bundan sonra, belirtilen özellikler Başlatıcı listesinde sunuldukları sırada başlatılır.  
  
 Başlatıcı listesindeki her başlatma, sınıfın bir üyesine ilk değer atamasından oluşur. Üyelerin adları ve veri türleri, sınıf tanımlandığında belirlenir. Aşağıdaki örneklerde, `Customer` sınıfı bulunmalı ve dize değerlerini kabul edebilecek ve `City` adlı `Name` üyelere sahip olmalıdır.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Alternatif olarak, aşağıdaki kodu kullanarak aynı sonucu elde edebilirsiniz:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Bu bildirimlerin her biri, parametresiz `Customer` oluşturucuyu kullanarak bir nesne oluşturan aşağıdaki örneğe eşdeğerdir ve ardından bir `Name` `With` ' ı kullanarak ve `City` özellikleri için başlangıç değerlerini belirtir Ekstre.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Sınıfı için `Name`bir değer içinde göndermenizi sağlayan parametreli bir Oluşturucu içeriyorsa, örneğin, aşağıdaki yollarla bir `Customer` nesneyi de bildirip başlatabilirsiniz: `Customer`  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Aşağıdaki kodda gösterildiği gibi tüm özellikleri başlatmak zorunda değilsiniz.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Ancak, başlatma listesi boş olamaz. Başlatılmamış özellikler varsayılan değerlerini korurlar.  
  
### <a name="type-inference-with-named-types"></a>Adlandırılmış türlerle tür çıkarımı  
 Nesne başlatıcılarının ve yerel tür çıkarımını birleştirerek `cust1` bildirimi için kodu kısaltabilirsiniz. Bu, değişken bildiriminde `As` yan tümceyi atlamanızı sağlar. Değişkenin veri türü, atama tarafından oluşturulan nesnenin türünden algılanır. Aşağıdaki örnekte, türü `cust6` ' dir. `Customer`  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Adlandırılmış türler hakkında açıklamalar  
  
- Bir sınıf üyesi, nesne başlatıcısı listesinde birden çok kez başlatılamaz. Bildirimi bir hataya `cust7` neden olur.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- Bir üye, kendisini veya başka bir alanı başlatmak için kullanılabilir. Bir üyeye, için `cust8`aşağıdaki bildirimde olduğu gibi, başlatılmadan önce erişiliyorsa, varsayılan değer kullanılacaktır. Bir nesne Başlatıcısı kullanan bir bildirim işlendiğinde, gerçekleşen ilk şey uygun oluşturucunun çağrılmakta olduğunu unutmayın. Bundan sonra, Başlatıcı listesindeki ayrı alanlar başlatılır. Aşağıdaki örneklerde için `Name` varsayılan değeri için `cust8`atanır ve başlatılmış bir değer içinde `cust9`atanır.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     Aşağıdaki `cust3` örnek, ve ' `cust4` `cust10` den'`cust11`i bildirmek ve başlatmak için parametreli oluşturucuyu kullanır.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Nesne başlatıcıları iç içe olabilir. `AddressClass` Aşağıdaki örnekte, iki `City` özelliği olan ve `State` `Customer` sınıfının bir `Address` örneği`AddressClass`olan bir özelliğine sahip olan bir sınıftır.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- Başlatma listesi boş olamaz.  
  
- Başlatılan örnek Object türünde olamaz.  
  
- Başlatılan sınıf üyeleri, paylaşılan Üyeler, salt okuma üyeleri, sabitler veya yöntem çağrıları olamaz.  
  
- Başlatılan sınıf üyeleri dizinlenemez veya nitelenmiyor. Aşağıdaki örnekler derleyici hatalarını yükseltir:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler, açıkça tanımlamadığınız ve isimsiz olmayan yeni türlerin örneklerini oluşturmak için nesne başlatıcıları kullanır. Bunun yerine, derleyici, nesne başlatıcısı listesinde belirleyeceğiniz özelliklere göre bir tür üretir. Türün adı belirtilmediğinden, *anonim bir tür*olarak adlandırılır. Örneğin, aşağıdaki bildirimi ile için `cust6`daha önceki bir ile karşılaştırın.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Tek fark sözdizimi, veri türü için sonrasında `New` hiçbir adın belirtilme türüdür. Ancak, ne olur oldukça farklıdır. Derleyici, `Name` ve `City`' ı iki özelliği olan yeni bir anonim türü tanımlar ve belirtilen değerlerle bir örneği oluşturur. Tür çıkarımı, dizeler gibi `Name` örnekte `City` ve türlerini belirler.  
  
> [!CAUTION]
> Anonim türün adı derleyici tarafından oluşturulur ve derlemeden derlemeye değişiklik gösterebilir. Kodunuz, anonim bir türün adını kullanmamalıdır veya bu adı kullanmalıdır.  
  
 Türün adı kullanılamadığından, öğesini bildirmek `As` `cust13`için bir yan tümce kullanamazsınız. Türü çıkarsanmalıdır. Bu, geç bağlama kullanılmadan, anonim türlerin kullanımını yerel değişkenlere kısıtlar.  
  
 Anonim türler sorgular için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kritik destek sağlar. Sorgularda anonim türlerin kullanımı hakkında daha fazla bilgi için, bkz. Visual Basic [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) ve [lınq 'ye giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Anonim türler hakkında açıklamalar  
  
- Genellikle, anonim bir tür bildirimindeki özelliklerin tümü veya çoğu, özellik adının önüne anahtar sözcüğü `Key` yazılarak belirtilen temel özelliklerdir.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Anahtar özellikleri hakkında daha fazla bilgi için bkz. [anahtar](../../../../visual-basic/language-reference/modifiers/key.md).  
  
- Adlandırılmış türler gibi, anonim tür tanımlarının başlatıcı listeleri en az bir özellik bildirmelidir.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- Anonim türün bir örneği bildirildiğinde, derleyici eşleşen bir anonim tür tanımı oluşturur. Özelliklerin adları ve veri türleri örnek bildiriminden alınır ve tanımda derleyici tarafından dahil edilir. Adlandırılmış bir tür için olduklarından özellikler önceden adlandırılmaz ve önceden tanımlanmamıştır. Türleri algılanır. Bir `As` yan tümce kullanarak özelliklerin veri türlerini belirtemezsiniz.  
  
- Anonim türler, özelliklerinin adlarını ve değerlerini birkaç farklı yolla de kurabilir. Örneğin, anonim bir tür özelliği bir değişkenin adını ve değerini ya da başka bir nesnenin özelliğinin adını ve değerini alabilir.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Anonim türlerde özellikleri tanımlamaya yönelik seçenekler hakkında daha fazla bilgi için bkz [. nasıl yapılır: Anonim tür bildirimlerinde](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)özellik adlarını ve türleri çıkarçıkar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Anonim tür bildirimlerinde özellik adlarını ve türleri çıkarçıkar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Nasıl yapılır: Nesne Başlatıcısı kullanarak nesne bildirme](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
