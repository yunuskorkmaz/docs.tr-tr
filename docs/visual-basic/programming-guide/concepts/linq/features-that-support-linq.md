---
title: LINQ'i Destekleyen Visual Basic Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 557e3607443066a863946ff08958197a14662a88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519408"
---
# <a name="visual-basic-features-that-support-linq"></a>LINQ'i Destekleyen Visual Basic Özellikleri
Adı [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] Visual Basic'de sorgu söz dizimi destekler ve doğrudan dilinde diğer dil yapıları teknoloji ifade eder. İle [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], dış veri kaynağına karşı sorgu için yeni bir dil öğrenmek gerekmez. İlişkisel veritabanlarını, XML depoları veya nesneleri verilere karşı Visual Basic kullanarak sorgulayabilirsiniz. Sorgu dili özellikleri, bu tümleştirme, sözdizimi hataları ve tür güvenliği için derleme zamanı denetimi sağlar. Visual Basic'te, çeşitli zengin sorguları yazma bilmek zorunda çoğunu zaten bildiğiniz Bu tümleştirme de sağlar.  
  
 Aşağıdaki bölümlerde, tanıtım belgeler, kod örnekleri ve örnek uygulamalar okuma kullanmaya başlamak sağlamak için yeterli ayrıntı LINQ destekleyen dil yapıları açıklanmaktadır. Nasıl dil özellikleri birlikte dil açısından tümleştirilmiş sorgunun etkinleştirmek için gelen, daha ayrıntılı açıklamaları bulmak için bağlantıları tıklatabilirsiniz. Başlamak için iyi bir yerdir [izlenecek yol: Visual Basic'de sorgu yazma](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Sorgu İfadeleri  
 Visual Basic'de sorgu ifadeleri, SQL veya XQuery benzer bir bildirim temelli söz diziminde ifade edilebilir. Derleme zamanında sorgu söz dizimi bir LINQ Sağlayıcısı'nın uygulamasında standart sorgu işleci genişletme yöntemleri, yöntem çağrılarını dönüştürülür. Standart sorgu işleçleri ile uygun bir ad belirterek kapsamda olan uygulamaların denetimi bir `Imports` deyimi. Visual Basic sorgu ifadesi söz dizimi şu şekilde görünür:  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Daha fazla bilgi için [Visual Basic'te LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Türü örtük olarak belirlenmiş değişkenleri  
 Bildirme ve bir değişkeni başlatarak, açıkça bir tür belirtmek yerine, derleyicinin çıkarır ve atamak etkinleştirebilirsiniz. Bu olarak adlandırılır *yerel tür çıkarımı*.  
  
 Eşleşen türleri için oluşturulan değişkenler, türü, açıkça belirtmediğiniz değişkenleri gibi yalnızca kesin olarak belirlenmiştir. Yalnızca bir yöntem gövdesi içinde yerel bir değişken tanımlarken yerel tür çıkarımı çalışır. Daha fazla bilgi için [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Aşağıdaki örnek, yerel tür çıkarımı gösterir. Bu örneği kullanmak için ayarlamalısınız `Option Infer` için `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Yerel tür çıkarımı Ayrıca, daha sonra bu bölümde açıklanan ve LINQ sorguları için gerekli olan anonim türler oluşturmak mümkün kılar.  
  
 LINQ aşağıdaki örnekte, tür çıkarımı meydana gelir `Option Infer` ya da `On` veya `Off`. Bir derleme zamanı hatası oluşur `Option Infer` olduğu `Off` ve `Option Strict` olduğu `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Nesne başlatıcıları  
 Nesne başlatıcıları bir sorgunun sonuçlarını tutmak için anonim bir tür oluşturmak için sahip sorgu ifadelerinde kullanılır. Adlandırılmış türleri sorguları dışında nesnelerini başlatmak için de kullanılabilir. Nesne Başlatıcı kullanarak açıkça bir oluşturucu çağırmaya gerek kalmadan tek bir satırda bir nesne başlatabilirsiniz. Adlı bir sınıf sahip olduğunuz varsayılarak `Customer` ortak olan `Name` ve `Phone` özelliklerini bu şekilde bir nesne Başlatıcı diğer özellikleriyle birlikte kullanılabilir:  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Daha fazla bilgi için [nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler, geçici olarak bir sorgu sonucunda dahil etmek istediğiniz öğenin içine bir özellikler kümesini gruplamak için kullanışlı bir yol sağlar. Bu öğe için bir adlandırılmış veri türü tanımlanmadan sorgusunda herhangi bir sırada kullanılabilir alanlar herhangi bir birleşimini seçmenize olanak sağlar.  
  
 Bir *anonim tür* derleyici tarafından dinamik olarak oluşturulur. Tür adı derleyici tarafından atanır ve yeni her derleme ile değişebilir. Bu nedenle, adı doğrudan kullanılamaz. Anonim türler aşağıdaki yolla başlatılır:  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Uzantı Metotları  
 Genişletme yöntemleri, bir veri türü ya da tanımının dışında arabiriminden yöntemler sağlar. Bu özellik, aslında türü değiştirmeden yeni yöntemler varolan bir türünü eklemek sağlar. Standart sorgu işleçleri kendilerini sağlayan genişletme yöntemleri kümesini olan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliğini uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>. Diğer uzantılar <xref:System.Collections.Generic.IEnumerable%601> dahil <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, ve <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 Bir yazdırma yöntemi aşağıdaki genişletme yöntemini ekleyen <xref:System.String> sınıfı.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 Yöntem gibi bir sıradan örnek yöntemi çağrıldığında <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Daha fazla bilgi için [genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Bir lambda ifadesi, hesaplar ve tek bir değer döndüren bir adı olmayan bir işlevdir. Adlandırılan işlevlerin, bir lambda ifadesi tanımlanabilir ve aynı zamanda yürütülür. Aşağıdaki örnek, 4 görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Lambda ifadesi tanımında bir değişken adına atamak ve ardından işlev çağrısı için adını kullanın. Aşağıdaki örnek, ayrıca 4 görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], lambda ifadeleri, birçok standart sorgu işleçlerinin temelini oluşturan. Temel sorgu yöntemleri gibi tanımlanmış olan hesaplamalar yakalamak için lambda ifadeleri derleyici oluşturur `Where`, `Select`, `Order By`, `Take While`ve diğerleri.  
  
 Örneğin, aşağıdaki kod, tüm üst düzey Öğrenciler Öğrenciler listesinden döndüren bir sorgu tanımlar.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 Sorgu tanımı için bağımsız değişkenlerini belirtmek için iki lambda ifadeleri kullanır aşağıdaki örneğe benzer bir kod derlenir `Where` ve `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Her iki sürümü kullanılarak çalıştırılabilir bir `For Each` döngü:  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Daha fazla bilgi için [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Visual Basic'te lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
