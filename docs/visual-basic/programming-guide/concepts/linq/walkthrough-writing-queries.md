---
title: Sorgu Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 6a9f229697ce3d6328c6fb09d18d4cc2627eab10
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351023"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Sorgu Yazma

Bu izlenecek yol, [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu ifadeleri yazmak için Visual Basic dil özelliklerini nasıl kullanabileceğinizi gösterir. İzlenecek yol, öğrenci nesneleri listesinde sorgu oluşturmayı, sorguların nasıl çalıştırılacağını ve bunların nasıl değiştirileceğini gösterir. Sorgular, nesne başlatıcıları, yerel tür çıkarımı ve anonim türler dahil olmak üzere çeşitli özellikler birleştirilir.

Bu yönergeyi tamamladıktan sonra, ilgilendiğiniz belirli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıya yönelik örneklere ve belgelere geçiş yapmaya hazırlanacaktır. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcılar [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]içerir.

## <a name="create-a-project"></a>Proje oluşturma

### <a name="to-create-a-console-application-project"></a>Konsol uygulama projesi oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Yüklü şablonlar** listesinde **Visual Basic**' a tıklayın.

4. Proje türleri listesinde **konsol uygulaması**' na tıklayın. **Ad** kutusuna proje için bir ad yazın ve ardından **Tamam**' a tıklayın.

    Bir proje oluşturulur. Varsayılan olarak, System. Core. dll öğesine bir başvuru içerir. Ayrıca, başvurular sayfasında **Içeri aktarılan ad alanları** listesi [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) <xref:System.Linq?displayProperty=nameWithType> ad alanını içerir.

5. [Derleme sayfasında, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), **seçenek çıkarımı seçeneğinin** **Açık**olarak ayarlandığından emin olun.

## <a name="add-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı ekleme

Bu izlenecek yolda bulunan sorguların veri kaynağı, `Student` nesnelerinin bir listesidir. Her `Student` nesnesi bir ad, soyadı, bir sınıf yılı ve öğrenci gövdesinde akademik bir derecelendirme içerir.

### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için

- Bir `Student` sınıfı tanımlayın ve sınıf örneklerinin bir listesini oluşturun.

  > [!IMPORTANT]
  > `Student` sınıfını tanımlamak ve İzlenecek yol örneklerinde kullanılan listeyi oluşturmak için gereken kod, [nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)bölümünde verilmiştir. Buradan kopyalayabilir ve projenize yapıştırabilirsiniz. Yeni kod, projeyi oluştururken görüntülenen kodun yerini alır.

### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir öğrenci eklemek için

- `Student` sınıfının başka bir örneğini listeye eklemek için `getStudents` yöntemindeki kalıbı izleyin. Öğrenci eklemek sizi nesne başlatıcılarına tanıtacaktır. Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).

## <a name="create-a-query"></a>Sorgu oluşturma

Yürütüldüğünde, bu bölüme eklenen sorgu, akademik derecesi bunları en üstteki on 'a yerleştiren öğrencilerin bir listesini oluşturur. Sorgu her seferinde tüm `Student` nesnesini seçtiği için, sorgu sonucunun türü `IEnumerable(Of Student)`. Ancak sorgu türü sorgu tanımlarında genellikle belirtilmez. Bunun yerine, derleyici türü tespit etmek için yerel tür çıkarımı kullanır. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Sorgunun Aralık değişkeni `currentStudent`, `students`içindeki her bir nesnenin özelliklerine erişim sağlayan `students`kaynaktaki her bir `Student` örneğine başvuru işlevi görür.

### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için

1. Aşağıdaki şekilde işaretlenen projenin `Main` yönteminde yer bulun:

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    Aşağıdaki kodu kopyalayın ve içine yapıştırın.

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. Derleyici tarafından atanan türün `IEnumerable(Of Student)`olduğunu doğrulamak için fare işaretçisini kodunuzda `studentQuery` üzerinde bekletin.

## <a name="run-the-query"></a>Sorguyu çalıştır

`studentQuery` değişkeni sorgu çalıştırmanın sonuçlarını değil sorgunun tanımını içerir. Sorgu çalıştırmaya yönelik tipik bir mekanizma `For Each` döngüdür. Döndürülen dizideki her öğeye döngü yineleme değişkeni üzerinden erişilir. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).

### <a name="to-run-the-query"></a>Sorguyu çalıştırmak için

1. Aşağıdaki `For Each` döngüsünü projenizdeki sorgunun altına ekleyin.

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. Veri türünü görmek için fare işaretçisini döngü denetimi değişkeninin üzerine `studentRecord`. `studentQuery` `Student` örneklerinin bir koleksiyonunu döndürdüğünden `studentRecord` türü `Student`olarak algılanır.

3. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

## <a name="modify-the-query"></a>Sorguyu Değiştirme

Sorgu sonuçlarının belirtilen sırada olmaları durumunda taranması daha kolay olur. Döndürülen sırayı kullanılabilir herhangi bir alana göre sıralayabilirsiniz.

### <a name="to-order-the-results"></a>Sonuçları sıralamak için

1. Aşağıdaki `Order By` yan tümcesini sorgunun `Where` deyimi ve `Select` deyimi arasına ekleyin. `Order By` yan tümcesi, her öğrencinin son adına göre sonuçları A 'dan Z 'ye sıralar.

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. Son ada göre sıralamak ve sonra adı için sorguya her iki alanı da ekleyin:

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    Ayrıca, Z 'den A 'ya sıralama için `Descending` belirtebilirsiniz.

3. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

### <a name="to-introduce-a-local-identifier"></a>Yerel tanımlayıcı tanıtmak için

1. Sorgu ifadesinde yerel bir tanımlayıcı tanıtmak için bu bölümdeki kodu ekleyin. Yerel tanımlayıcı bir ara sonuç tutacaktır. Aşağıdaki örnekte `name`, öğrencinin adı ve soyadlarını bir kez birleştirme tutan bir tanımlayıcıdır. Yerel bir tanımlayıcı kolaylık sağlaması için kullanılabilir veya daha önce birden çok kez hesaplanabilecek bir ifadenin sonuçlarını depolayarak performansı geliştirebilir.

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

### <a name="to-project-one-field-in-the-select-clause"></a>Select yan tümcesinde bir alan planlamak için

1. Öğeleri kaynaktaki öğelerden farklı olan bir dizi üreten bir sorgu oluşturmak için bu bölümden sorgu ve `For Each` döngüsünü ekleyin. Aşağıdaki örnekte, kaynak bir `Student` nesneleri koleksiyonudur, ancak her bir nesnenin yalnızca bir üyesi döndürülür: Soyacıadı olan öğrencilerin ilk adı. `currentStudent.First` bir dize olduğundan, `studentQuery3` tarafından döndürülen sıranın veri türü `IEnumerable(Of String)`, dizeler dizisi olur. Önceki örneklerde olduğu gibi, `studentQuery3` için bir veri türü ataması, derleyicinin yerel tür çıkarımı kullanılarak belirlenmesi için bırakılır.

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. Atanan türün `IEnumerable(Of String)`olduğunu doğrulamak için fare işaretçisini kodunuzda `studentQuery3` üzerinde bekletin.

3. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select yan tümcesinde anonim bir tür oluşturmak için

1. Anonim türlerin sorgularda nasıl kullanıldığını görmek için bu bölümden kodu ekleyin. Verileri, veri kaynağından, tüm kayıtlar (önceki örneklerde`currentStudent` kayıtlar) veya tek alanlar (önceki bölümde`First`) yerine birden çok alan döndürmek istediğinizde bu sorguları sorgular halinde kullanırsınız. Sonuca eklemek istediğiniz alanları içeren yeni bir adlandırılmış tür tanımlamak yerine, `Select` yan tümcesindeki alanları belirtirsiniz ve derleyici, özellikleri olarak bu alanlarla anonim bir tür oluşturur. Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

    Aşağıdaki örnek, akademik derecelendirmesi sırasında akademik derecesi 1 ile 10 arasında olan Seniors 'in adını ve derecesini döndüren bir sorgu oluşturur. Bu örnekte, `Select` yan tümcesi anonim bir türün bir örneğini döndürdüğünden ve anonim bir türün kullanılabilir bir adı olmadığı için `studentQuery4` türü çıkarsanmalıdır.

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

## <a name="additional-examples"></a>Ek Örnekler

Temel bilgileri anladığınıza göre, aşağıda [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularının esnekliğini ve gücünü gösteren ek örneklerin bir listesi verilmiştir. Her örnek öncesinde ne yapabileceğinize ilişkin kısa bir açıklamadır. Gösterilen türü görmek için fare işaretçisini her sorgu için sorgu sonuç değişkeninin üzerine getirin. Sonuçları oluşturmak için bir `For Each` döngüsü kullanın.

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a>Ek Bilgiler

Sorgularla çalışmanın temel kavramlarıyla ilgili bilgi sahibi olduktan sonra, ilgilendiğiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı türü için belge ve örnekleri okumaya hazırsınızdır:

- [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)

- [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Visual Basic LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
