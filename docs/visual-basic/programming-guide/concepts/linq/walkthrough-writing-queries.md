---
title: Sorgu Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 25905d7ac3ca4bb66a22ad1df421b400eaa6b08f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413277"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Sorgu Yazma

Bu izlenecek yol, dil ile tümleşik sorgu (LINQ) sorgu ifadeleri yazmak için Visual Basic dil özelliklerini nasıl kullanabileceğinizi gösterir. İzlenecek yol, öğrenci nesneleri listesinde sorgu oluşturmayı, sorguların nasıl çalıştırılacağını ve bunların nasıl değiştirileceğini gösterir. Sorgular, nesne başlatıcıları, yerel tür çıkarımı ve anonim türler dahil olmak üzere çeşitli özellikler birleştirilir.

Bu yönergeyi tamamladıktan sonra, ilgilendiğiniz belirli bir LINQ sağlayıcısı için örneklere ve belgelere geçiş yapmaya hazırlanacaktır. LINQ sağlayıcıları [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , LINQ to DataSet ve içerir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .

## <a name="create-a-project"></a>Proje oluşturma

### <a name="to-create-a-console-application-project"></a>Konsol uygulama projesi oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Yüklü şablonlar** listesinde **Visual Basic**' a tıklayın.

4. Proje türleri listesinde **konsol uygulaması**' na tıklayın. **Ad** kutusuna proje için bir ad yazın ve ardından **Tamam**' a tıklayın.

    Bir proje oluşturulur. Varsayılan olarak, System. Core. dll öğesine bir başvuru içerir. Ayrıca, başvurular sayfasında **Içeri aktarılan ad alanları** listesi [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) <xref:System.Linq?displayProperty=nameWithType> ad alanını içerir.

5. [Derleme sayfasında, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), **seçenek çıkarımı seçeneğinin** **Açık**olarak ayarlandığından emin olun.

## <a name="add-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı ekleme

Bu izlenecek yolda bulunan sorguların veri kaynağı bir `Student` nesne listesidir. Her `Student` nesne bir ad, soyadı, bir sınıf yılı ve öğrenci gövdesinde akademik bir derecelendirme içerir.

### <a name="to-add-the-data-source"></a>Veri kaynağını eklemek için

- Bir `Student` sınıf tanımlayın ve sınıf örneklerinin bir listesini oluşturun.

  > [!IMPORTANT]
  > `Student`Sınıfını tanımlamak ve İzlenecek yol örneklerinde kullanılan listeyi oluşturmak için gereken kod, [nasıl yapılır: öğe listesi oluşturma](how-to-create-a-list-of-items.md)bölümünde verilmiştir. Buradan kopyalayabilir ve projenize yapıştırabilirsiniz. Yeni kod, projeyi oluştururken görüntülenen kodun yerini alır.

### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir öğrenci eklemek için

- `getStudents`Bir sınıfın başka bir örneğini listeye eklemek için yöntemindeki kalıbı izleyin `Student` . Öğrenci eklemek sizi nesne başlatıcılarına tanıtacaktır. Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).

## <a name="create-a-query"></a>Sorgu oluşturma

Yürütüldüğünde, bu bölüme eklenen sorgu, akademik derecesi bunları en üstteki on 'a yerleştiren öğrencilerin bir listesini oluşturur. Sorgu `Student` her seferinde tüm nesneyi seçtiğinden, sorgu sonucunun türü olur `IEnumerable(Of Student)` . Ancak sorgu türü sorgu tanımlarında genellikle belirtilmez. Bunun yerine, derleyici türü tespit etmek için yerel tür çıkarımı kullanır. Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../language-features/variables/local-type-inference.md). Sorgunun Aralık değişkeni, `currentStudent` kaynak içindeki her bir örneğe bir başvuru olarak görev yapar ve `Student` `students` içindeki her nesnenin özelliklerine erişim sağlar `students` .

### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için

1. `Main`Aşağıdaki şekilde işaretlenen projenin yönteminde yer bulun:

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    Aşağıdaki kodu kopyalayın ve içine yapıştırın.

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. `studentQuery`Derleyici tarafından atanan türün olduğunu doğrulamak için fare işaretçisini kodunuzda bekletin `IEnumerable(Of Student)` .

## <a name="run-the-query"></a>Sorguyu çalıştır

Değişkeni, `studentQuery` sorgunun çalıştırıldığı sonuçları değil sorgunun tanımını içerir. Sorgu çalıştırmaya yönelik tipik bir mekanizma bir `For Each` döngüdür. Döndürülen dizideki her öğeye döngü yineleme değişkeni üzerinden erişilir. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](writing-your-first-linq-query.md).

### <a name="to-run-the-query"></a>Sorguyu çalıştırmak için

1. Aşağıdaki `For Each` döngüyü projenizdeki sorgunun altına ekleyin.

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. Veri türünü görmek için fare işaretçisini döngü denetim değişkeninin üzerine getirin `studentRecord` . Öğesinin türü olarak `studentRecord` algılanır `Student` , çünkü `studentQuery` bir örnek koleksiyonu döndürür `Student` .

3. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

## <a name="modify-the-query"></a>Sorguyu Değiştirme

Sorgu sonuçlarının belirtilen sırada olmaları durumunda taranması daha kolay olur. Döndürülen sırayı kullanılabilir herhangi bir alana göre sıralayabilirsiniz.

### <a name="to-order-the-results"></a>Sonuçları sıralamak için

1. Aşağıdaki `Order By` yan tümceyi, `Where` ve sorgusunun deyimi arasına ekleyin `Select` . `Order By`Yan tümcesi, her öğrencinin son adına göre sonuçları a 'Dan Z 'ye sıralar.

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. Son ada göre sıralamak ve sonra adı için sorguya her iki alanı da ekleyin:

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    Ayrıca, `Descending` Z 'Den A 'ya sıralama belirtebilirsiniz.

3. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

### <a name="to-introduce-a-local-identifier"></a>Yerel tanımlayıcı tanıtmak için

1. Sorgu ifadesinde yerel bir tanımlayıcı tanıtmak için bu bölümdeki kodu ekleyin. Yerel tanımlayıcı bir ara sonuç tutacaktır. Aşağıdaki örnekte, `name` öğrencinin adı ve soyadlarını bir kez birleştirme tutan bir tanımlayıcıdır. Yerel bir tanımlayıcı kolaylık sağlaması için kullanılabilir veya daha önce birden çok kez hesaplanabilecek bir ifadenin sonuçlarını depolayarak performansı geliştirebilir.

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

### <a name="to-project-one-field-in-the-select-clause"></a>Select yan tümcesinde bir alan planlamak için

1. `For Each`Öğeleri kaynaktaki öğelerden farklı olan bir dizi üreten bir sorgu oluşturmak için bu bölümden sorgu ve döngüyü ekleyin. Aşağıdaki örnekte, kaynak bir `Student` nesne koleksiyonudur, ancak her bir nesnenin yalnızca bir üyesi döndürülür: son adı Garcia olan öğrencilerin ilk adı. Çünkü `currentStudent.First` bir dizedir, tarafından döndürülen sıranın veri türü `studentQuery3` `IEnumerable(Of String)` , dizeler dizisi. Önceki örneklerde olduğu gibi, için bir veri türü ataması, `studentQuery3` derleyicinin yerel tür çıkarımı kullanılarak belirlenmesi için bırakılır.

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. `studentQuery3`Atanan türün olduğunu doğrulamak için fare işaretçisini kodunuzda bekletin `IEnumerable(Of String)` .

3. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select yan tümcesinde anonim bir tür oluşturmak için

1. Anonim türlerin sorgularda nasıl kullanıldığını görmek için bu bölümden kodu ekleyin. Veri kaynağından, tüm kayıtlar ( `currentStudent` Önceki örneklerde kayıtlar) veya tek alanlar (önceki bölümde) yerine birden fazla alan döndürmek istediğinizde bunları sorgularda kullanırsınız `First` . Sonuca eklemek istediğiniz alanları içeren yeni bir adlandırılmış tür tanımlamak yerine, `Select` yan tümcesindeki alanları belirtirsiniz ve derleyici, özellikleri olarak bu alanlarla anonim bir tür oluşturur. Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).

    Aşağıdaki örnek, akademik derecelendirmesi sırasında akademik derecesi 1 ile 10 arasında olan Seniors 'in adını ve derecesini döndüren bir sorgu oluşturur. Bu örnekte, `studentQuery4` `Select` yan tümce anonim bir türün bir örneğini döndürdüğünden ve anonim bir türün kullanılabilir bir adı olmadığından, türü çıkarsanmalıdır.

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. CTRL + F5 tuşlarına basarak uygulamayı derleyin ve çalıştırın. Konsol penceresindeki sonuçları aklınızda edin.

## <a name="additional-examples"></a>Ek Örnekler

Temel bilgileri anladığınıza göre, LINQ sorgularının esnekliğini ve gücünü göstermek için ek örneklerin bir listesi aşağıda verilmiştir. Her örnek öncesinde ne yapabileceğinize ilişkin kısa bir açıklamadır. Gösterilen türü görmek için fare işaretçisini her sorgu için sorgu sonuç değişkeninin üzerine getirin. `For Each`Sonuçları oluşturmak için bir döngü kullanın.

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a>Ek Bilgi

Sorgularla çalışmanın temel kavramlarıyla ilgili bilgi sahibi olduktan sonra, ilgilendiğiniz LINQ sağlayıcısı türü için belge ve örnekleri okumaya hazırsınızdır:

- [Nesnelere LINQ](linq-to-objects.md)

- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)

- [LINQ - XML](linq-to-xml.md)

- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)
- [Visual Basic'te LINQ'e Başlarken](getting-started-with-linq.md)
- [Yerel Tür Arabirimi](../../language-features/variables/local-type-inference.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonim Türler](../../language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic'de LINQ'e Giriş](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Sorgular](../../../language-reference/queries/index.md)
