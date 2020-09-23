---
title: LINQ 'i destekleyen özellikler
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: bd63cd36c1f85fd89349293a71ecc5b281165380
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078313"
---
# <a name="visual-basic-features-that-support-linq"></a>LINQ'i Destekleyen Visual Basic Özellikleri

Dil ile tümleşik sorgu (LINQ), sorgu söz dizimini ve diğer dil yapılarını doğrudan dilde destekleyen Visual Basic teknolojiden başvurur. LINQ ile, bir dış veri kaynağında sorgulama yapmak için yeni bir dil öğreninizin olması gerekmez. Visual Basic kullanarak ilişkisel veritabanlarındaki, XML mağazalarındaki veya nesnelerdeki verilere göre sorgulama yapabilirsiniz. Bu dile sorgu yeteneklerini tümleştirme, sözdizimi hataları ve tür güvenliği için derleme zamanı denetimini sunar. Bu tümleştirme Ayrıca, Visual Basic içinde zengin, değişen sorgular yazmak için bilmeniz gerekenleri zaten öğrenmenizi de sağlar.  
  
 Aşağıdaki bölümlerde, giriş belgelerini, kod örneklerini ve örnek uygulamaları okumaya başlamanıza olanak tanımak için LINQ 'i destekleyen dil yapıları açıklanır. Ayrıca, dil özelliklerinin, dil ile tümleşik sorguyu etkinleştirmek için nasıl bir araya geldiği hakkında daha ayrıntılı açıklamalar bulmak için bağlantılara tıklayabilirsiniz. Başlamak için iyi bir yer [Izlenecek yol: Visual Basic sorguları yazma](walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Sorgu İfadeleri  

 Visual Basic sorgu ifadeleri SQL veya XQuery ile benzer bir bildirime dayalı sözdiziminde ifade edilebilir. Derleme zamanında sorgu sözdizimi, bir LINQ sağlayıcısının standart sorgu işleci genişletme yöntemlerinin uygulamasına yönelik yöntem çağrılarına dönüştürülür. Uygulamalar, ilgili ad alanını bir ifadesiyle belirterek hangi standart sorgu işleçlerinin kapsamda olduğunu denetler `Imports` . Visual Basic sorgu ifadesinin sözdizimi şuna benzer:  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC LINQ 'e giriş](../../language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Örtük olarak yazılan değişkenler  

 Bir değişkeni bildirdiğinizde ve başlattığınızda açıkça bir tür belirtmek yerine, derleyicinin türü çıkarması ve atamasını sağlayabilirsiniz. Bu, *Yerel tür çıkarımı*olarak adlandırılır.  
  
 Türleri çıkarılan değişkenler, türü açıkça belirttiğiniz değişkenler gibi kesin şekilde türdedir. Yerel tür çıkarımı yalnızca bir yöntem gövdesi içinde yerel bir değişken tanımladığınızda kullanılır. Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../language-features/variables/local-type-inference.md).  
  
 Aşağıdaki örnekte yerel tür çıkarımı gösterilmektedir. Bu örneği kullanmak için, olarak ayarlamanız gerekir `Option Infer` `On` .  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 Yerel tür çıkarımı Ayrıca, bu bölümün ilerleyen kısımlarında açıklanan ve LINQ sorguları için gerekli olan anonim türler oluşturmayı da mümkün kılar.  
  
 Aşağıdaki LINQ örneğinde, ya da ise tür çıkarımı oluşur `Option Infer` `On` `Off` . , Ve ise bir derleme zamanı hatası `Option Infer` oluşur `Off` `Option Strict` `On` .  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Nesne başlatıcıları  

 Nesne başlatıcıları, bir sorgunun sonuçlarını tutmak için anonim bir tür oluşturmanız gerektiğinde sorgu ifadelerinde kullanılır. Bunlar ayrıca, adlandırılmış türdeki nesneleri sorgular dışında başlatmak için de kullanılabilir. Bir nesne Başlatıcısı kullanarak, bir oluşturucuyu açıkça çağırmadan tek bir satırdaki nesneyi başlatabilirsiniz. `Customer`Ortak ve özelliklerine sahip olan adlı bir sınıfınız olduğunu varsayarak `Name` `Phone` , diğer özelliklerle birlikte, bir nesne Başlatıcısı bu şekilde kullanılabilir:  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  

 Anonim türler, bir dizi özelliği bir sorgu sonucuna eklemek istediğiniz bir öğeye geçici olarak gruplandırmak için kullanışlı bir yol sağlar. Bu, sorguda bulunan kullanılabilir alanların herhangi bir birleşimini, öğe için adlandırılmış bir veri türü tanımlamadan herhangi bir sırada seçmenizi sağlar.  
  
 *Anonim bir tür* , derleyici tarafından dinamik olarak oluşturulur. Türün adı derleyici tarafından atanır ve her yeni derleme ile değişebilir. Bu nedenle, ad doğrudan kullanılamaz. Anonim türler aşağıdaki şekilde başlatılır:  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Uzantı Metotları  

 Uzantı yöntemleri, tanım dışından bir veri türüne veya arabirime Yöntemler eklemenizi sağlar. Bu özellik, aslında türü değiştirmeden mevcut bir türe yeni yöntemler eklemenizi sağlar. Standart sorgu işleçleri, uygulayan herhangi bir tür için LINQ sorgu işlevselliği sağlayan bir genişletme yöntemleri kümesidir <xref:System.Collections.Generic.IEnumerable%601> . <xref:System.Collections.Generic.IEnumerable%601>, Ve dahil olmak üzere diğer uzantılar <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Intersect%2A> .  
  
 Aşağıdaki genişletme yöntemi sınıfına bir Print yöntemi ekler <xref:System.String> .  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 Yöntemi sıradan bir örnek yöntemi gibi çağrılır <xref:System.String> :  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda İfadeleri  

 Lambda ifadesi tek bir değer hesaplayan ve döndüren adı olmayan bir işlevdir. Adlandırılmış işlevlerin aksine, bir lambda ifadesi aynı anda tanımlanabilir ve çalıştırılabilir. Aşağıdaki örnek 4 ' ü görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Lambda ifadesi tanımını bir değişken adına atayabilir ve sonra işlevi çağırmak için adı kullanabilirsiniz. Aşağıdaki örnek ayrıca 4 görüntüler.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 LINQ 'ta, lambda ifadeleri standart sorgu işleçlerinin birçoğunu daha az bir şekilde ifade ediyor. Derleyici,,, ve gibi temel sorgu yöntemlerinde tanımlanmış hesaplamaları yakalamak için lambda ifadeleri oluşturur `Where` `Select` `Order By` `Take While` .  
  
 Örneğin, aşağıdaki kod, öğrenciler listesinden tüm kıdemli öğrenciler döndüren bir sorgu tanımlar.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 Sorgu tanımı, ve için bağımsız değişkenleri belirtmek üzere iki lambda ifadesi kullanan aşağıdaki örneğe benzer kodla derlenir `Where` `Select` .  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 Her iki sürüm de bir döngü kullanılarak çalıştırılabilir `For Each` :  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Daha fazla bilgi için bkz. [lambda ifadeleri](../../language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)
- [Visual Basic'te LINQ'e Başlarken](getting-started-with-linq.md)
- [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)
- [Option Infer Deyimi](../../../language-reference/statements/option-infer-statement.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
