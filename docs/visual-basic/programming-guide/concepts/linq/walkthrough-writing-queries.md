---
title: Visual Basic'de sorgu yazma
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 6c5f7d288d805a6a25afa9a5b32a4550aaa76ec3
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275359"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Sorgu Yazma
Bu izlenecek yol yazmak için Visual Basic dil özellikleri nasıl kullanabileceğinizi gösterir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu ifadelerinde. İzlenecek yol, sorgu Öğrenci nesnelerin listesini oluşturma, sorgularının nasıl çalıştırılacağını ve bunları değiştirmek nasıl gösterir. Sorguları nesne başlatıcıları, yerel tür çıkarımı ve anonim türler dahil olmak üzere çeşitli özelliklerini bir araya getirin.  
  
 Bu kılavuzu tamamladıktan sonra belirli belgeleri ve örnekleri taşımaya hazır olmayacak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ilgilendiğiniz sağlayıcısı. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları içerir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Proje oluşturma  
  
#### <a name="to-create-a-console-application-project"></a>Konsol uygulama projesi oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  İçinde **yüklü şablonlar** listesinde **Visual Basic**.  
  
4.  Proje türleri listesinde tıklayın **konsol uygulaması**. İçinde **adı** kutusuna proje için bir ad yazın ve ardından **Tamam**.  
  
     Bir Proje oluşturulur. Varsayılan olarak, bir System.Core.dll başvurusu içerir. Ayrıca, **içeri aktarılan ad alanlarını** listesini [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) içerir <xref:System.Linq?displayProperty=nameWithType> ad alanı.  
  
5.  Üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), emin **Option Infer** ayarlanır **üzerinde**.  
  
## <a name="add-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı ekleme  
 Veri kaynağını sorgular için bu kılavuzda bir listesidir `Student` nesneleri. Her `Student` nesne, ad, Soyadı, sınıf yıl ve bir Akademik Öğrenci gövdesi derece içerir.  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağı eklemek için  
  
-   Tanımlayan bir `Student` sınıfı ve sınıf örneklerinin bir listesini oluşturun.  
  
    > [!IMPORTANT]
    >  Tanımlamak için gereken kodu `Student` sınıfı ve kullanılan liste oluşturma izlenecek yolda örnekler sağlanır [nasıl yapılır:, bir liste öğesi oluşturun](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Buradan kopyalayın ve projenize yapıştırın. Projeyi oluşturduğunuzda görünen kodu yeni kodu değiştirir.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir öğrenci eklemek için  
  
-   Düzende izleyin `getStudents` başka bir örneğini ekleme yöntemi `Student` listesine sınıfı. Bir öğrenci eklemek için nesne başlatıcıları başlatacaktır. Daha fazla bilgi için [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Sorgu oluşturma  
 Çalıştırıldığında, bu bölüme eklendiğinden sorgu, akademik derece bunları en iyi on koyar Öğrenciler listesini oluşturur. Sorgu tam seçer çünkü `Student` sorgu sonuç türü her zaman nesnedir `IEnumerable(Of Student)`. Ancak, sorgu türü genellikle sorgu tanımlarında belirtilmedi. Bunun yerine, derleyici yerel tür çıkarımı türünü belirlemek için kullanır. Daha fazla bilgi için [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Sorgunun aralık değişkeni `currentStudent`, her bir başvuru olarak hizmet veren `Student` kaynak örneğinde `students`, her bir nesnenin özelliklerini erişim sağlamaya `students`.  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
1.  Bir yerde bulmanızı `Main` şu şekilde işaretlenmiş projenin yöntemi:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Aşağıdaki kodu kopyalayın ve yapıştırın.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Üzerine fare işaretçisini `studentQuery` derleyici tarafından atanan türü olduğunu doğrulamak için kodunuzda `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Sorguyu çalıştır  
 Değişken `studentQuery` sorgu, sorgu çalıştırmanın sonuçlarını değil tanımını içerir. Bir sorgu çalıştırmak için tipik bir mekanizma bir `For Each` döngü. Döndürülen dizideki her öğe döngüsünün yineleme değişkeni erişilir. Sorgu yürütme hakkında daha fazla bilgi için bkz: [bilgisayarınızı ilk LINQ sorgusu yazma](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Sorguyu çalıştırmak için  
  
1.  Aşağıdaki `For Each` projenizi sorguda aşağıdaki döngü.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  Fare işaretçisini döngü denetim değişkeni `studentRecord` veri türünü görmek için. Türünü `studentRecord` olmasını çıkarılan `Student`, çünkü `studentQuery` koleksiyonunu döndürür `Student` örnekleri.  
  
3.  Derleme ve CTRL + F5 tuşlarına basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
 Belirli bir sırada olmaları durumunda tarama sorgu sonuçlarını daha kolaydır. Tüm kullanılabilir alana göre döndürülen dizi sıralayabilirsiniz.  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1.  Aşağıdaki `Order By` arasında yan tümcesi `Where` deyimi ve `Select` sorgu deyimi. `Order By` Yan tümcesi sipariş sonuçları alfabetik olarak A'dan Z'ye, son her öğrencinin adına göre.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Son adı ve ardından ilk adına göre sıralamak için her iki alanı sorguya ekleyin:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Ayrıca belirtebileceğiniz `Descending` sipariş Z'den A'ya için  
  
3.  Derleme ve CTRL + F5 tuşlarına basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
#### <a name="to-introduce-a-local-identifier"></a>Yerel tanımlayıcı tanıtmak için  
  
1.  Sorgu ifadesi içinde yerel tanımlayıcı tanıtmak için bu bölümdeki kod ekleyin. Yerel tanımlayıcı bir ara sonucunu tutacaktır. Aşağıdaki örnekte, `name` dizilerin bir bitiştirmesi olan Öğrenci tutan bir tanımlayıcı ilk ve son adları. Aksi takdirde birden çok kez hesaplanan bir ifadenin sonuçlarını depolayarak performansını artırabilir veya yerel tanımlayıcı kolaylık sağlamak için kullanılabilir.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Derleme ve CTRL + F5 tuşlarına basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Select yan tümcesinde bir alan planlamak için  
  
1.  Sorguya ekleyin ve `For Each` öğeleri farklı kaynaktaki öğelerinden bir dizi üretir bir sorgu oluşturmak için bu bölümdeki döngü. Aşağıdaki örnekte, bir kaynak koleksiyonudur `Student` nesneleri, ancak her bir nesnenin yalnızca bir üye döndürülür: Soyadı olan Garcia Öğrenciler adı. Çünkü `currentStudent.First` bir dize veri türü tarafından döndürülen dizinin `studentQuery3` olduğu `IEnumerable(Of String)`, bir dize sırası. Önceki örneklerde olduğu gibi bir veri atamasını türü `studentQuery3` yerel tür çıkarımı kullanarak belirlemek derleyicinin bırakılır.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Üzerine fare işaretçisini `studentQuery3` atanan türü olduğunu doğrulamak için kodunuzda `IEnumerable(Of String)`.  
  
3.  Derleme ve CTRL + F5 tuşlarına basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select yan tümcesinde anonim bir tür oluşturmak için  
  
1.  Nasıl anonim türler görmek için bu bölümü koddan sorgularında kullanılan ekleyin. Çeşitli alanları veri kaynağı tüm kayıtların yerine döndürülecek istediğinizde bunları sorguları içinde kullanabilirsiniz (`currentStudent` önceki örneklerde, kayıtlarını) veya tek alanları (`First` önceki bölümde). Sonuçta dahil etmek istediğiniz alanları içeren yeni bir adlandırılmış tür tanımlama yerine alanlarda belirtin `Select` yan tümcesi ve derleyici özelliklerini olarak bu alanlara sahip bir anonim tür oluşturur. Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Aşağıdaki örnek, boyut sayısı 1 ile 10, akademik derece sırasına göre akademik derece arasındadır seniors ve adını döndüren sorgu oluşturur. Bu örnekte, türü `studentQuery4` çünkü anlaşılmalıdır `Select` yan tümcesi, anonim bir türün örneğini döndürür ve anonim bir tür kullanılabilir adı yok.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Derleme ve CTRL + F5 tuşlarına basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
## <a name="additional-examples"></a>Ek Örnekler  
 Temelleri anladığınıza göre gücü ve esnekliği göstermek için ek örnekler listesi aşağıda verilmiştir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular. Her örneğin ne işe yaradığını kısa bir açıklaması tarafından gelmelidir. Fare işaretçisini çıkarsanan tür görmek her bir sorgu için sorgu sonucu değişkenine üzerine bırakın. Kullanım bir `For Each` döngü, istediğiniz sonuçları vermeyebilir.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Ek Bilgiler  
 Sorgularla çalışma temel kavramları hakkında bilgi sahibi olduktan sonra belgeler ve örnekler için belirli türünü okumak hazır olursunuz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ilgilendiğiniz sağlayıcısı:  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
- [Visual Basic'te lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
