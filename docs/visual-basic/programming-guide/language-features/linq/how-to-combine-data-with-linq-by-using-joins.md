---
title: 'Nasıl yapılır: birleştirmeleri kullanarak verileri LINQ ile birleştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344995"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme (Visual Basic)
Visual Basic, Koleksiyonlar arasındaki ortak değerlere bağlı olarak birden çok koleksiyonun içeriğini birleştirmenize olanak tanımak için `Join` ve `Group Join` sorgu yan tümcelerini sağlar. Bu değerler *anahtar* değerleri olarak bilinir. İlişkisel veritabanı kavramlarıyla tanıdık geliştiriciler `Join` yan tümcesini bir Iç BIRLEŞIM ve `Group Join` yan tümcesi, etkin bir şekilde sol dış BIRLEŞIM olarak tanır.  
  
 Bu konudaki örneklerde `Join` ve `Group Join` sorgu yan tümcelerini kullanarak verileri birleştirmenin birkaç yolu gösterilmektedir.  
  
## <a name="create-a-project-and-add-sample-data"></a>Proje oluşturma ve örnek veri ekleme  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Örnek veri ve türleri içeren bir proje oluşturmak için  
  
1. Bu konudaki örnekleri çalıştırmak için, Visual Studio 'Yu açın ve yeni bir Visual Basic konsol uygulaması projesi ekleyin. Visual Basic tarafından oluşturulan Module1. vb dosyasını çift tıklayın.  
  
2. Bu konudaki örnekler, aşağıdaki kod örneğinde `Person` ve `Pet` türlerini ve verilerini kullanır. Bu kodu, Visual Basic tarafından oluşturulan varsayılan `Module1` modüle kopyalayın.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirme  
 Bir Iç BIRLEŞIM, verileri iki koleksiyondan birleştirir. Belirtilen anahtar değerlerinin eşleştiği öğeler dahil edilir. Diğer koleksiyonda eşleşen bir öğeye sahip olmayan her türlü öğe hariç tutulur.  
  
 Visual Basic, LINQ bir Iç BIRLEŞIM gerçekleştirmeye yönelik iki seçenek sunar: örtük bir birleşim ve açık birleşim.  
  
 Örtük bir katılım, bir `From` yan tümcesine katılacak koleksiyonları belirtir ve bir `Where` yan tümcesinde eşleşen anahtar alanlarını tanımlar. Visual Basic, belirtilen anahtar alanları temelinde iki koleksiyonu örtülü olarak birleştirir.  
  
 Birleşimde hangi anahtar alanlarının kullanılacağı konusunda özel olmasını istediğiniz zaman, `Join` yan tümcesini kullanarak açık bir JOIN belirleyebilirsiniz. Bu durumda, sorgu sonuçlarını filtrelemek için bir `Where` yan tümcesi hala kullanılabilir.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirmek için  
  
1. Hem örtük hem de açık iç birleşim örneklerini görmek için aşağıdaki kodu projenizdeki `Module1` modüle ekleyin.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirme  
 SOL dış BIRLEŞIM, birleştirmenin sol taraftaki koleksiyonundan tüm öğeleri ve yalnızca birleştirmenin sağ taraftaki koleksiyonundan eşleşen değerleri içerir. Sol taraftaki koleksiyonda eşleşen bir öğeye sahip olmayan birleştirmenin sağ taraftaki koleksiyonundan herhangi bir öğe sorgu sonucundan çıkarılır.  
  
 `Group Join` yan tümcesi, bir sol dış BIRLEŞIMI etkili bir şekilde gerçekleştirir. Genellikle bir sol dış BIRLEŞIM olarak bilinen ve `Group Join` yan tümcesinin döndürdüğü fark, `Group Join` yan tümcesinin, sol taraftaki koleksiyondaki her öğe için birleştirmenin sağ taraftaki koleksiyonundan sonuçlar vermesinin ne olduğunu gösteren fark. İlişkisel bir veritabanında, bir sol dış BIRLEŞIM, sorgu sonucundaki her bir öğenin JOIN içindeki her iki koleksiyondan eşleşen öğeler içerdiği Gruplandırılmamış bir sonuç döndürür. Bu durumda, birleştirmenin sol taraftaki koleksiyonundaki öğeler, her eşleşen öğe için sağ taraftaki koleksiyondan yinelenir. Sonraki yordamı tamamladığınızda bunun nasıl göründüğünü görürsünüz.  
  
 Bir `Group Join` sorgusunun sonuçlarını, gruplanmış her sorgu sonucu için bir öğe döndürecek şekilde genişleterek, Gruplandırılmamış bir sonuç olarak alabilirsiniz. Bunu gerçekleştirmek için, gruplandırılmış koleksiyonun `DefaultIfEmpty` yönteminde sorgulama yapmanız gerekir. Bu, birleştirmenin sol taraftaki koleksiyonundan gelen öğelerin, sağ taraftaki koleksiyondan eşleşen bir sonuçları olmasa bile sorgu sonucuna dahil edilmesini sağlar. Birleştirmenin sağ taraftaki koleksiyonundan eşleşen bir değer olmadığında varsayılan bir sonuç değeri sağlamak için sorgunuza kod ekleyebilirsiniz.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirmek için  
  
1. Hem gruplanmış bir sol dış birleşimin hem de Gruplandırılmamış bir sol dış birleşimin örneklerini görmek için aşağıdaki kodu projenizdeki `Module1` modüle ekleyin.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Bileşik anahtar kullanarak bir JOIN gerçekleştirme  
 Katılmakta olan koleksiyonlardan değerleri eşleştirirken kullanılacak birden çok anahtar alanını tanımlamak için bir `Join` veya `Group Join` yan tümcesindeki `And` anahtar sözcüğünü kullanabilirsiniz. `And` anahtar sözcüğü belirtilen tüm anahtar alanlarının birleştirilecek öğelerin eşleşmesi gerektiğini belirtir.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Bileşik anahtar kullanarak bir JOIN gerçekleştirmek için  
  
1. Bileşik anahtar kullanan bir birleşimin örneklerini görmek için, aşağıdaki kodu projenizdeki `Module1` modüle ekleyin.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Kodu çalıştırma  
  
#### <a name="to-add-code-to-run-the-examples"></a>Örnekleri çalıştırmak için kod eklemek için  
  
1. Bu konudaki örnekleri çalıştırmak için projenizdeki `Module1` modülündeki `Sub Main` aşağıdaki kodla değiştirin.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Örnekleri çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From Yan Tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ (C#) Ile veri dönüştürmeleri](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
