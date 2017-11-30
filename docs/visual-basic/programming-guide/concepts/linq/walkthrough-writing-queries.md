---
title: Visual Basic'de sorgu yazma
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: "70"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 00103fe95912ba44a764cef30b337603301c8479
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Sorgu Yazma
Bu kılavuzda yazmak için Visual Basic dil özellikleri nasıl kullanabileceğinizi gösterir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu ifadeleri. İzlenecek yol Öğrenci nesnelerin bir listesini sorgu oluşturma, sorguları çalıştırmak nasıl ve bunları değiştirme gösterilir. Sorguları nesne başlatıcılar, yerel türü çıkarımı ve anonim türler de dahil olmak üzere çeşitli özellikler dahil.  
  
 Bu kılavuzu tamamladıktan sonra örnekler ve belirli belgeler için geçmek hazır olacak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ilgilendiğiniz sağlayıcısı. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sağlayıcıları dahil [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Proje oluşturma  
  
#### <a name="to-create-a-console-application-project"></a>Konsol uygulama projesi oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
3.  İçinde **yüklü şablonlar** tıklatın **Visual Basic**.  
  
4.  Proje türleri listesinde tıklatın **konsol uygulaması**. İçinde **adı** kutusunda, proje için bir ad yazın ve ardından **Tamam**.  
  
     Bir Proje oluşturulur. Varsayılan olarak, bu System.Core.dll başvuru içeriyor. Ayrıca, **içeri aktarılan ad alanları** listesini [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) içeren <xref:System.Linq?displayProperty=nameWithType> ad alanı.  
  
5.  Üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), emin **Option Infer** ayarlanır **üzerinde**.  
  
## <a name="add-an-in-memory-data-source"></a>Bellek İçi Veri Kaynağı ekleme  
 Bu kılavuzda sorguları için veri kaynağı listesidir `Student` nesneleri. Her `Student` nesnesini içeren bir ad, Soyadı, bir sınıf yılın ve bir Akademik Öğrenci gövde derece.  
  
#### <a name="to-add-the-data-source"></a>Veri kaynağı eklemek için  
  
-   Tanımlayan bir `Student` sınıfı ve sınıfının örneklerinin bir listesini oluşturun.  
  
    > [!IMPORTANT]
    >  Tanımlamak için gerekli kod `Student` sınıfı ve kullanılan liste oluşturma kılavuzda örnekler sağlanır [nasıl yapılır: öğelerinin listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Buradan kopyalayın ve bunu projenize yapıştırın. Yeni kodunu projeyi oluşturduğunuzda görünen kodu değiştirir.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Öğrenciler listesine yeni bir öğrenci eklemek için  
  
-   Düzende izleyin `getStudents` başka bir örneği eklemek için yöntemini `Student` listesine sınıfı. Öğrenci ekleme nesne başlatıcıları tanıtılacaktır. Daha fazla bilgi için bkz: [nesne başlatıcıları: adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Bir sorgu oluşturun  
 Çalıştırıldığında, bu bölümde eklenen sorgu, akademik derece bunları ilk on koyar Öğrenciler listesini oluşturur. Sorgu tam seçer çünkü `Student` her zaman, sorgunun sonuç türü nesnesidir `IEnumerable(Of Student)`. Ancak, sorgu türü sorgu tanımlarında genellikle belirtilmedi. Bunun yerine, derleyici yerel türü çıkarımı türü belirlemek için kullanır. Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Sorgunun aralık değişkeni `currentStudent`, her bir başvuru olarak hizmet veren `Student` kaynak örneğinde `students`, her nesnenin özelliklerini erişim sağlayan `students`.  
  
#### <a name="to-create-a-simple-query"></a>Basit bir sorgu oluşturmak için  
  
1.  Yerinde Bul `Main` şu şekilde işaretlenir projesinin yöntemi:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Aşağıdaki kodu kopyalayın ve yapıştırın.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Üzerinden fare işaretçisini `studentQuery` derleyici atanan türü olduğunu doğrulamak için kodunuzda `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Sorguyu çalıştır  
 Değişkeni `studentQuery` sorgu, sorgu çalıştırmanın sonuçlarını değil tanımını içerir. Bir sorgu çalıştırmak için tipik bir mekanizmadır bir `For Each` döngü. Döndürülen dizideki her öğe döngü yineleme değişkeni erişilir. Sorgu yürütme hakkında daha fazla bilgi için bkz: [yazma bilgisayarınızı ilk LINQ sorgusu](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Sorguyu çalıştırmak için  
  
1.  Aşağıdakileri ekleyin `For Each` döngü projenizdeki sorgu aşağıda.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  For döngüsü denetim değişkeni fare işaretçisini `studentRecord` veri türünü görmek için. Türü `studentRecord` olmasını olayla `Student`, çünkü `studentQuery` koleksiyonunu döndürür `Student` örnekleri.  
  
3.  Oluşturma ve CTRL + F5'e basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
## <a name="modify-the-query"></a>Sorguyu Değiştirme  
 Belirli bir sırada olmaları durumunda tarama sorgu sonuçlarını daha kolaydır. Döndürülen dizi tüm kullanılabilir alana göre sıralayabilirsiniz.  
  
#### <a name="to-order-the-results"></a>Sonuçları sıralamak için  
  
1.  Aşağıdakileri ekleyin `Order By` yan tümcesi arasında `Where` deyimi ve `Select` sorgu ifadesi. `Order By` Yan tümcesi sipariş sonuçları alfabetik olarak A'dan Z'ye, son her öğrencinin adını göre.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Soyadı ve sonra ilk adına göre sıralamak için her iki alan sorguya ekleyin:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Ayrıca belirtebilirsiniz `Descending` Z siparişe A. için  
  
3.  Oluşturma ve CTRL + F5'e basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
#### <a name="to-introduce-a-local-identifier"></a>Yerel tanımlayıcı tanıtmak için  
  
1.  Bu bölümdeki yerel bir tanımlayıcı sorgu ifadesinde tanıtmak için kodu ekleyin. Yerel tanımlayıcı bir ara sonuç tutar. Aşağıdaki örnekte, `name` Öğrenci birleşimini tutan bir tanımlayıcı ilk ve son adları. Aksi takdirde birden çok kez hesaplanan bir ifadenin sonuçlarını depolayarak performansını artırabilir veya yerel bir tanımlayıcı kolaylık sağlamak için kullanılabilir.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Oluşturma ve CTRL + F5'e basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Select yan tümcesinde bir alan planlamak için  
  
1.  Sorguyu eklemek ve `For Each` öğeleri farklı kaynak öğelerinden bir dizi üreten bir sorgu oluşturmak için bu bölümü döngüden. Aşağıdaki örnekte, kaynak topluluğudur `Student` nesneleri, ancak her nesnenin yalnızca bir üye döndürülür: Soyadı olan Garcia Öğrenciler adı. Çünkü `currentStudent.First` bir dize veri türü tarafından döndürülen sıra `studentQuery3` olan `IEnumerable(Of String)`, bir dizi dize. Önceki örneklerde olduğu gibi bir veri atama türü `studentQuery3` yerel türü çıkarımı kullanarak belirlemek derleyici için bırakılır.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Üzerinden fare işaretçisini `studentQuery3` atanan türü olduğunu doğrulamak için kodunuzda `IEnumerable(Of String)`.  
  
3.  Oluşturma ve CTRL + F5'e basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select yan tümcesinde anonim bir tür oluşturmak için  
  
1.  Nasıl anonim türlerini görmek için bu bölümdeki kod sorgularda kullanılan ekleyin. Veri kaynağı tam kayıtları yerine birkaç alanları döndürmek istediğinizde sorgularda kullanabilmek (`currentStudent` önceki örneklerde kayıtları) ya da tek alanları (`First` önceki bölümde). Sonuçta dahil etmek istediğiniz alanları içeren yeni bir adlandırılmış türü tanımlama yerine alanlarda belirtin `Select` yan tümcesi ve derleyici özelliklerini olarak bu alanlara sahip anonim bir tür oluşturur. Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Aşağıdaki örnek adını ve 1 ile 10 akademik derece sırasına göre akademik derece arasındadır seniors derecesini döndüren bir sorgu oluşturur. Bu örnekte, türü `studentQuery4` çünkü olayla gerekir `Select` yan tümcesi anonim bir türün bir örneği döndürür ve anonim bir tür kullanılabilir adı yok.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Oluşturma ve CTRL + F5'e basarak uygulamayı çalıştırın. Sonuçları konsol penceresinde unutmayın.  
  
## <a name="additional-examples"></a>Ek Örnekler  
 Temel kavramları anladığınıza göre gücü ve esnekliği göstermek için ek örnekler listesi aşağıdadır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular. Her örneğin ne yaptığını kısa bir açıklaması tarafından gelmelidir. Fare işaretçisini çıkarılan türü görmek her sorgu için sorgu sonucu değişkeni üzerine bırakın. Kullanım bir `For Each` sonuçlar döngü.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Ek Bilgiler  
 Sorguları ile çalışmanın temel kavramları hakkında bilgi sahibi olduktan sonra belgeler ve örnekler için belirli türünü okumak hazır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ilgilendiğiniz sağlayıcısı:  
  
 [Nesnelere LINQ](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ-SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ-DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Visual Basic'te Lınq'e Başlarken](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Sorguları](../../../../visual-basic/language-reference/queries/queries.md)
