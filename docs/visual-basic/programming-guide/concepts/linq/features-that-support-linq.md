---
title: LINQ'i Destekleyen Visual Basic Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: db2eff2f7c19a3c510e7b212f5bb406d7a885439
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-features-that-support-linq"></a>LINQ'i Destekleyen Visual Basic Özellikleri
Adı [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] teknolojisi Visual Basic'de sorgu sözdizimi destekler ve doğrudan dilde başka bir dil yapıları başvuruyor. İle [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], dış veri kaynağına karşı sorgu için yeni bir dil öğrenin gerekmez. İlişkisel veritabanları, XML depoları veya nesneler verileri karşı Visual Basic kullanarak sorgulayabilirsiniz. Bu tümleştirme dile sorgu özelliklerinin sözdizimi hataları ve tür güvenliği için derleme zamanı denetimini etkinleştirir. Bu tümleştirme, aynı zamanda Visual Basic'te zengin, çeşitli sorguları yazmaya bilmek zorunda çoğu zaten biliyor sağlar.  
  
 Aşağıdaki bölümlerde, tanıtım belgeler, kod örnekleri ve örnek uygulamalar okuma başlamak etkinleştirmek için yeterli ayrıntılı LINQ destekleyen dil yapıları açıklanmaktadır. Nasıl dil özellikleri birlikte dil ile tümleşik sorgu etkinleştirmek için gelen, daha ayrıntılı açıklamalar bulmak için bağlantıları tıklatabilirsiniz. Başlamak için uygun bir yerdir [izlenecek yol: Visual Basic'te yazma sorguları](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Sorgu İfadeleri  
 Visual Basic'de sorgu ifadeleri, SQL veya XQuery benzer bir tanımlayıcı sözdizimi ifade edilebilir. Derleme zamanında yöntem çağrılarını standart sorgu işleci genişletme yöntemleri LINQ sağlayıcının uygulaması için sorgu söz dizimi dönüştürülür. Standart sorgu işleçleri ile uygun ad belirterek kapsamındaki uygulamaları denetim bir `Imports` deyimi. Visual Basic sorgu ifade sözdizimi şu şekildedir:  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Daha fazla bilgi için bkz: [Visual Basic'te LINQ giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Türü örtük olarak belirlenmiş değişkenleri  
 Bildirme ve bir değişkeni başlatma zaman açıkça bir tür belirtmek yerine, derleyicinin Infer ve atamak etkinleştirebilirsiniz. Bu olarak adlandırılır *yerel türü çıkarımı*.  
  
 Değişkenleri, türleri algılanır kesinlikle, türünü açıkça belirtmek yalnızca değişkenler gibi yazılmalıdır. Yalnızca bir yöntem gövdesi içinde yerel bir değişken tanımlarken yerel türü çıkarımı çalışır. Daha fazla bilgi için bkz: [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Aşağıdaki örnek, yerel türü çıkarımı gösterilmektedir. Bu örneği kullanmak için ayarlamalısınız `Option Infer` için `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Yerel türü çıkarımı Ayrıca, daha sonra bu bölümde açıklanan ve LINQ sorguları için gerekli olan anonim türler oluşturmak mümkün kılar.  
  
 Aşağıdaki LINQ örnekte tür çıkarımı saptanmışsa `Option Infer` ya `On` veya `Off`. Derleme zamanı hata oluşur `Option Infer` olan `Off` ve `Option Strict` olan `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Nesne başlatıcıları  
 Bir sorgunun sonuçlarını tutmak için anonim bir tür oluşturmanız gerektiğinde nesne başlatıcıları sorgu ifadelerinde kullanılır. Adlandırılmış türleri sorguları dışında nesnelerin başlatmak için de kullanılabilir. Nesne Başlatıcı kullanarak bir oluşturucu açıkça çağırmadan nesneyi tek bir satıra başlatabilirsiniz. Adlı bir sınıf olduğunu varsaydığımızdan `Customer` ortak olan `Name` ve `Phone` özellikler, diğer özellikleri ile birlikte bu şekilde nesne Başlatıcı kullanılabilir:  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Daha fazla bilgi için bkz: [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler geçici olarak bir sorgu sonucunda dahil etmek istediğiniz bir öğenin içine özellikler kümesini gruplamak için kolay bir yol sağlamak. Bu öğe için bir adlandırılmış veri türü tanımlamadan sorgusunda herhangi bir sırada kullanılabilir alanlar herhangi bir birleşimini seçmenize olanak sağlar.  
  
 Bir *anonim tür* derleyici tarafından dinamik olarak oluşturulur. Türün adını derleyici tarafından atanır ve her yeni derleme ile değiştirebilirsiniz. Bu nedenle, adı doğrudan kullanılamaz. Anonim türleri aşağıdaki yolla başlatılır:  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Uzantı Metotları  
 Genişletme yöntemleri, bir veri türüne veya arabirimden tanımının dışında yöntemleri eklemenize olanak tanır. Bu özellik, etkin, yeni yöntemleri için mevcut bir türle türü değiştirmeden eklemek, sağlar. Standart sorgu işleçleri kendilerini sağlamak genişletme yöntemleri kümesidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliği uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>. Diğer uzantılar <xref:System.Collections.Generic.IEnumerable%601> dahil <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, ve <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 Bir yazdırma yöntemi aşağıdaki genişletme yöntemi ekleyen <xref:System.String> sınıfı.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 Bu yöntem gibi bir sıradan örneği yöntemi çağrıldığında <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Lambda ifadesi hesaplar ve tek bir değer döndüren bir ad olmadan bir işlevdir. Adlandırılmış işlevler, bir lambda ifadesi tanımlanabilir ve aynı anda yürütülen. Aşağıdaki örnek 4 görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Lambda ifadesi tanımı için bir değişken adı atamak ve bir işlevi çağırmak için adını kullanın. Aşağıdaki örnek 4 de görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], lambda ifadeleri standart sorgu işleçleri çoğunu temelini oluşturan. Temel sorgu yöntemleri gibi tanımlanan hesaplamalar yakalamak için lambda ifadeleri derleyici oluşturur `Where`, `Select`, `Order By`, `Take While`ve diğerleri.  
  
 Örneğin, aşağıdaki kod, tüm üst düzey Öğrenciler Öğrenciler listesinden döndüren bir sorgu tanımlar.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 Sorgu tanımı bağımsız değişkenleri belirtmek için iki lambda ifadeleri kullanır aşağıdaki örneğe benzer bir kod derlenir `Where` ve `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Her iki sürümünü kullanarak çalıştırabilirsiniz bir `For Each` döngü:  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Visual Basic'te Lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
