---
title: LINQ 'i destekleyen özellikler
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 57c0566f9a76715e48b20f2e6493aa1a506c64be
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636867"
---
# <a name="visual-basic-features-that-support-linq"></a>LINQ'i Destekleyen Visual Basic Özellikleri
Dil ile tümleşik sorgu (LINQ), sorgu söz dizimini ve diğer dil yapılarını doğrudan dilde destekleyen Visual Basic teknolojiden başvurur. LINQ ile, bir dış veri kaynağında sorgulama yapmak için yeni bir dil öğreninizin olması gerekmez. Visual Basic kullanarak ilişkisel veritabanlarındaki, XML mağazalarındaki veya nesnelerdeki verilere göre sorgulama yapabilirsiniz. Bu dile sorgu yeteneklerini tümleştirme, sözdizimi hataları ve tür güvenliği için derleme zamanı denetimini sunar. Bu tümleştirme Ayrıca, Visual Basic içinde zengin, değişen sorgular yazmak için bilmeniz gerekenleri zaten öğrenmenizi de sağlar.  
  
 Aşağıdaki bölümlerde, giriş belgelerini, kod örneklerini ve örnek uygulamaları okumaya başlamanıza olanak tanımak için LINQ 'i destekleyen dil yapıları açıklanır. Ayrıca, dil özelliklerinin, dil ile tümleşik sorguyu etkinleştirmek için nasıl bir araya geldiği hakkında daha ayrıntılı açıklamalar bulmak için bağlantılara tıklayabilirsiniz. Başlamak için iyi bir yer [Izlenecek yol: Visual Basic sorguları yazma](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Sorgu İfadeleri  
 Visual Basic sorgu ifadeleri SQL veya XQuery ile benzer bir bildirime dayalı sözdiziminde ifade edilebilir. Derleme zamanında sorgu sözdizimi, bir LINQ sağlayıcısının standart sorgu işleci genişletme yöntemlerinin uygulamasına yönelik yöntem çağrılarına dönüştürülür. Uygulamalar, bir `Imports` ifadesiyle uygun ad alanını belirterek hangi standart sorgu işleçlerinin kapsamda olduğunu denetler. Visual Basic sorgu ifadesinin sözdizimi şuna benzer:  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Örtük olarak yazılan değişkenler  
 Bir değişkeni bildirdiğinizde ve başlattığınızda açıkça bir tür belirtmek yerine, derleyicinin türü çıkarması ve atamasını sağlayabilirsiniz. Bu, *Yerel tür çıkarımı*olarak adlandırılır.  
  
 Türleri çıkarılan değişkenler, türü açıkça belirttiğiniz değişkenler gibi kesin şekilde türdedir. Yerel tür çıkarımı yalnızca bir yöntem gövdesi içinde yerel bir değişken tanımladığınızda kullanılır. Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Aşağıdaki örnekte yerel tür çıkarımı gösterilmektedir. Bu örneği kullanmak için `Option Infer` `On`ayarlamanız gerekir.  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 Yerel tür çıkarımı Ayrıca, bu bölümün ilerleyen kısımlarında açıklanan ve LINQ sorguları için gerekli olan anonim türler oluşturmayı da mümkün kılar.  
  
 Aşağıdaki LINQ örneğinde, `Option Infer` `On` veya `Off`olduğunda tür çıkarımı oluşur. `Option Infer` `Off` ve `Option Strict` `On`olduğunda bir derleme zamanı hatası oluşur.  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Nesne başlatıcıları  
 Nesne başlatıcıları, bir sorgunun sonuçlarını tutmak için anonim bir tür oluşturmanız gerektiğinde sorgu ifadelerinde kullanılır. Bunlar ayrıca, adlandırılmış türdeki nesneleri sorgular dışında başlatmak için de kullanılabilir. Bir nesne Başlatıcısı kullanarak, bir oluşturucuyu açıkça çağırmadan tek bir satırdaki nesneyi başlatabilirsiniz. Ortak `Name` ve `Phone` özelliklerine sahip `Customer` adlı bir sınıfınız olduğunu varsayarak, diğer özelliklerle birlikte, bir nesne Başlatıcısı bu şekilde kullanılabilir:  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  
 Anonim türler, bir dizi özelliği bir sorgu sonucuna eklemek istediğiniz bir öğeye geçici olarak gruplandırmak için kullanışlı bir yol sağlar. Bu, sorguda bulunan kullanılabilir alanların herhangi bir birleşimini, öğe için adlandırılmış bir veri türü tanımlamadan herhangi bir sırada seçmenizi sağlar.  
  
 *Anonim bir tür* , derleyici tarafından dinamik olarak oluşturulur. Türün adı derleyici tarafından atanır ve her yeni derleme ile değişebilir. Bu nedenle, ad doğrudan kullanılamaz. Anonim türler aşağıdaki şekilde başlatılır:  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Genişletme Yöntemleri  
 Uzantı yöntemleri, tanım dışından bir veri türüne veya arabirime Yöntemler eklemenizi sağlar. Bu özellik, aslında türü değiştirmeden mevcut bir türe yeni yöntemler eklemenizi sağlar. Standart sorgu işleçleri, <xref:System.Collections.Generic.IEnumerable%601>uygulayan herhangi bir tür için LINQ sorgu işlevselliği sağlayan bir genişletme yöntemleri kümesidir. <xref:System.Collections.Generic.IEnumerable%601> diğer uzantılar <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>ve <xref:System.Linq.Enumerable.Intersect%2A>içerir.  
  
 Aşağıdaki genişletme yöntemi <xref:System.String> sınıfına bir Print yöntemi ekler.  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 Yöntemi, <xref:System.String>sıradan bir örnek yöntemi gibi çağrılır:  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  
 Lambda ifadesi tek bir değer hesaplayan ve döndüren adı olmayan bir işlevdir. Adlandırılmış işlevlerin aksine, bir lambda ifadesi aynı anda tanımlanabilir ve çalıştırılabilir. Aşağıdaki örnek 4 ' ü görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Lambda ifadesi tanımını bir değişken adına atayabilir ve sonra işlevi çağırmak için adı kullanabilirsiniz. Aşağıdaki örnek ayrıca 4 görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 LINQ 'ta, lambda ifadeleri standart sorgu işleçlerinin birçoğunu daha az bir şekilde ifade ediyor. Derleyici, `Where`, `Select`, `Order By`, `Take While`ve diğerleri gibi temel sorgu yöntemlerinde tanımlanmış hesaplamaları yakalamak için lambda ifadeleri oluşturur.  
  
 Örneğin, aşağıdaki kod, öğrenciler listesinden tüm kıdemli öğrenciler döndüren bir sorgu tanımlar.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 Sorgu tanımı, `Where` ve `Select`bağımsız değişkenlerini belirtmek için iki lambda ifadesi kullanan aşağıdaki örneğe benzer kodla derlenir.  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 Her iki sürüm de bir `For Each` döngüsü kullanılarak çalıştırılabilir:  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Daha fazla bilgi için bkz. [lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Visual Basic LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
