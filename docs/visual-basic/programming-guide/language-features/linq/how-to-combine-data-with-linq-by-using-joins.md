---
title: 'Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: de8c4ec3ab8a0f2335c034231c661380420fd31b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405010"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme (Visual Basic)
Visual Basic, `Join` ve `Group Join` sorgu yan tümcelerini, Koleksiyonlar arasındaki ortak değerlere göre birden çok koleksiyonun içeriğini birleştirmeniz için sağlar. Bu değerler *anahtar* değerleri olarak bilinir. İlişkisel veritabanı kavramlarını bilen geliştiriciler `Join` yan tümceyi BIR Iç birleşim ve `Group Join` yan tümce olarak, ETKIN BIR sol dış birleşim olarak tanır.  
  
 Bu konudaki örneklerde, `Join` ve sorgu yan tümcelerini kullanarak verileri birleştirmenin birkaç yolu gösterilmektedir `Group Join` .  
  
## <a name="create-a-project-and-add-sample-data"></a>Proje oluşturma ve örnek veri ekleme  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Örnek veri ve türleri içeren bir proje oluşturmak için  
  
1. Bu konudaki örnekleri çalıştırmak için, Visual Studio 'Yu açın ve yeni bir Visual Basic konsol uygulaması projesi ekleyin. Visual Basic tarafından oluşturulan Module1. vb dosyasını çift tıklayın.  
  
2. Bu konudaki örnekler, `Person` `Pet` Aşağıdaki kod örneğinde ve türlerini ve verilerini kullanır. Bu kodu, `Module1` Visual Basic tarafından oluşturulan varsayılan modüle kopyalayın.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirme  
 Bir Iç BIRLEŞIM, verileri iki koleksiyondan birleştirir. Belirtilen anahtar değerlerinin eşleştiği öğeler dahil edilir. Diğer koleksiyonda eşleşen bir öğeye sahip olmayan her türlü öğe hariç tutulur.  
  
 Visual Basic, LINQ bir Iç BIRLEŞIM gerçekleştirmeye yönelik iki seçenek sunar: örtük bir birleşim ve açık birleşim.  
  
 Örtük bir katılım, bir yan tümcesine katılacak koleksiyonları belirtir `From` ve bir yan tümcedeki eşleşen anahtar alanlarını tanımlar `Where` . Visual Basic, belirtilen anahtar alanları temelinde iki koleksiyonu örtülü olarak birleştirir.  
  
 `Join`Birleşimde hangi anahtar alanlarının kullanılacağı konusunda özel olmasını istediğinizde yan tümcesini kullanarak açık bir JOIN belirtebilirsiniz. Bu durumda, `Where` sorgu sonuçlarını filtrelemek için bir yan tümce hala kullanılabilir.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>JOIN yan tümcesini kullanarak bir Iç birleşim gerçekleştirmek için  
  
1. `Module1`Hem örtük hem de açık iç birleşim örneklerini görmek için aşağıdaki kodu projenizdeki modüle ekleyin.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirme  
 SOL dış BIRLEŞIM, birleştirmenin sol taraftaki koleksiyonundan tüm öğeleri ve yalnızca birleştirmenin sağ taraftaki koleksiyonundan eşleşen değerleri içerir. Sol taraftaki koleksiyonda eşleşen bir öğeye sahip olmayan birleştirmenin sağ taraftaki koleksiyonundan herhangi bir öğe sorgu sonucundan çıkarılır.  
  
 `Group Join`Yan tümce, BIR sol dış birleşimi etkili bir şekilde gerçekleştirir. Genellikle bir sol dış BIRLEŞIM olarak bilinen ve yan tümcesinin döndürdüğü farklar arasındaki fark, `Group Join` `Group Join` yan tümcesinin, sol taraftaki koleksiyondaki her öğe için birleştirmenin sağ tarafındaki koleksiyonundan sonuçlar vermesinin ne olduğunu ifade ediyor. İlişkisel bir veritabanında, bir sol dış BIRLEŞIM, sorgu sonucundaki her bir öğenin JOIN içindeki her iki koleksiyondan eşleşen öğeler içerdiği Gruplandırılmamış bir sonuç döndürür. Bu durumda, birleştirmenin sol taraftaki koleksiyonundaki öğeler, her eşleşen öğe için sağ taraftaki koleksiyondan yinelenir. Sonraki yordamı tamamladığınızda bunun nasıl göründüğünü görürsünüz.  
  
 Sorgu sonuçlarını `Group Join` her gruplanmış sorgu sonucu için bir öğe döndürecek şekilde genişleterek, bir sorgunun sonuçlarını Gruplandırılmamış bir sonuç olarak alabilirsiniz. Bunu gerçekleştirmek için, `DefaultIfEmpty` gruplandırılmış koleksiyonun yönteminde sorgulama yapmanız gerekir. Bu, birleştirmenin sol taraftaki koleksiyonundan gelen öğelerin, sağ taraftaki koleksiyondan eşleşen bir sonuçları olmasa bile sorgu sonucuna dahil edilmesini sağlar. Birleştirmenin sağ taraftaki koleksiyonundan eşleşen bir değer olmadığında varsayılan bir sonuç değeri sağlamak için sorgunuza kod ekleyebilirsiniz.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group JOIN yan tümcesini kullanarak bir sol dış birleşim gerçekleştirmek için  
  
1. `Module1`Hem gruplanmış bir sol dış birleşimin hem de Gruplandırılmamış bir sol dış birleşimin örneklerini görmek için aşağıdaki kodu projenizdeki modüle ekleyin.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Bileşik anahtar kullanarak bir JOIN gerçekleştirme  
 `And` `Join` `Group Join` Katılmakta olan koleksiyonlardan değerleri eşleştirirken kullanılacak birden çok anahtar alanını tanımlamak için bir veya yan tümcesindeki anahtar sözcüğünü kullanabilirsiniz. `And`Anahtar sözcüğü, birleştirilecek öğeler için belirtilen tüm anahtar alanlarının eşleşmesi gerektiğini belirtir.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Bileşik anahtar kullanarak bir JOIN gerçekleştirmek için  
  
1. `Module1`Birleşik anahtar kullanan bir birleşimin örneklerini görmek için aşağıdaki kodu projenizdeki modüle ekleyin.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Kodu çalıştırma  
  
#### <a name="to-add-code-to-run-the-examples"></a>Örnekleri çalıştırmak için kod eklemek için  
  
1. `Sub Main` `Module1` Bu konudaki örnekleri çalıştırmak için projenizdeki modülün içindeki modülünü aşağıdaki kodla değiştirin.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Örnekleri çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](index.md)
- [Visual Basic'de LINQ'e Giriş](introduction-to-linq.md)
- [JOIN yan tümcesi](../../../language-reference/queries/join-clause.md)
- [Group Join Yan Tümcesi](../../../language-reference/queries/group-join-clause.md)
- [From yan tümcesi](../../../language-reference/queries/from-clause.md)
- [WHERE yan tümcesi](../../../language-reference/queries/where-clause.md)
- [Sorgular](../../../language-reference/queries/index.md)
- [LINQ ile Veri Dönüştürmeler (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
