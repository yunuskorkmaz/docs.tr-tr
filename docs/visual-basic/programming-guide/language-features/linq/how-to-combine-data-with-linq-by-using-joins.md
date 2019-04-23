---
title: 'Nasıl yapılır: (Visual Basic) birleştirmeleri kullanarak verileri LINQ ile birleştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 127e1afa7707f31584e93f3d4b08e865d7fcedf6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319605"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Nasıl yapılır: (Visual Basic) birleştirmeleri kullanarak verileri LINQ ile birleştirme
Visual Basic sağlar `Join` ve `Group Join` sorgu yan tümceleri sağlamak koleksiyonları arasında ortak değerlere göre birden fazla koleksiyonun içeriğini birleştirmek. Bu değerler olarak bilinen *anahtar* değerleri. Geliştiricileri ilişkisel veritabanı kavramlarını tanıdık algılayacağı `Join` INNER JOIN as yan tümcesi ve `Group Join` olarak etkili bir şekilde, LEFT OUTER JOIN yan tümcesi.  
  
 Bu konudaki örnekler birkaç yolu kullanarak verileri birleştirme gösterir `Join` ve `Group Join` sorgu yan tümceleri.  
  
## <a name="create-a-project-and-add-sample-data"></a>Bir proje oluşturun ve örnek veriler ekleyin  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Örnek veriler ve türlerini içeren bir proje oluşturmak için  
  
1. Bu konudaki örnek çalıştırmak için Visual Studio'yu açın ve yeni bir Visual Basic konsol uygulaması projesi ekleyin. Visual Basic tarafından oluşturulan Module1.vb dosyasını çift tıklayın.  
  
2. Bu konuda kullanım örnekleri `Person` ve `Pet` türleri ve verileri aşağıdaki kod örneği. Varsayılan bu kodu kopyalayın `Module1` Visual Basic ile oluşturulan modül.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Join yan tümcesi iç birleşim gerçekleştirmek  
 INNER JOIN iki koleksiyon birleştirir. Kendisi için belirtilen anahtar değerlerine eşleşen öğe dahil edilir. Eşleşen bir öğeyi diğer koleksiyonda olmayan tüm koleksiyonlardan biri öğeleri hariç tutulur.  
  
 Visual Basic'te LINQ iç birleşim gerçekleştirmek için iki seçenek sağlar: örtük bir birleştirme ve açık bir birleştirme.  
  
 Dolaylı bir birleşim katılması koleksiyonları belirtir bir `From` yan tümcesi ve eşleşen anahtar alanları tanımlayan bir `Where` yan tümcesi. Visual Basic, örtük olarak belirtilen anahtar alanlara göre iki koleksiyon birleştirir.  
  
 Açık bir birleşim kullanarak belirtebilirsiniz `Join` birleştirme işleminde kullanmak için hangi anahtar alanları belirli olmasını istediğiniz zaman yan tümcesi. Bu durumda, bir `Where` yan tümcesi yine de sorgu sonuçları filtrelemek için kullanılabilir.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>INNER JOIN JOIN yan tümcesi kullanarak gerçekleştirmek için  
  
1. Aşağıdaki kodu ekleyin `Module1` iki örtük ve açık iç birleşim örneklerini görmek için projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group Join tümcesi bir sol dış birleşim gerçekleştirmek  
 SOL dış birleştirme sol taraftaki koleksiyonunun tüm öğeleri birleştirme ve yalnızca eşleşen değerler birleşimin sağ taraftaki koleksiyonunun içerir. Sol taraftaki koleksiyonda eşleşen öğe yok öğeleri birleşimin sağ taraftaki koleksiyonunun sorgu sonucu hariç tutulur.  
  
 `Group Join` Yan tümcesi gerçekleştirir, aslında LEFT OUTER JOIN. LEFT OUTER JOIN genellikle bilinen ve hangi arasındaki fark `Group Join` yan tümcesi döndürür da `Group Join` yan tümcesi grupları sonuçları birleştirme sol taraftaki koleksiyondaki her öğe için sağ taraftaki koleksiyonu. İlişkisel bir veritabanında, her öğe, sorgu sonucu Gruplandırılmamış bir sonuç her iki koleksiyon birleştirme eşleşen öğeleri içeren bir LEFT OUTER JOIN döndürür. Bu durumda, sağ taraftaki koleksiyonunun eşleşen her öğe için bir birleşimin sol taraftaki koleksiyonun öğelerinden yinelenir. Sonraki yordamı tamamladıktan sonra göründüğüne görürsünüz.  
  
 Sonuçlarını almak bir `Group Join` her gruplandırılmış sorgu sonucu için bir öğe döndürmek için sorguyu genişleterek Gruplandırılmamış bir sonucu olarak sorgu. Bunu yapmak için üzerinde sorgulama emin olmak sahip `DefaultIfEmpty` gruplandırılmış koleksiyonun yöntemi. Bu, sağ taraftaki koleksiyonunun eşleşen sonuç yok olsa bile bir birleşimin sol taraftaki koleksiyonun öğeleri yine de sorgu sonucuna eklenir sağlar. Sorgunuzu birleşimin sağ taraftaki koleksiyonunun eşleşen hiçbir değer olduğunda bir varsayılan sonuç değeri sağlamak için kod ekleyebilirsiniz.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Left Outer JOIN gruba katılma yan tümcesini kullanarak gerçekleştirmek için  
  
1. Aşağıdaki kodu ekleyin `Module1` gruplandırılmış bir sol dış birleşim hem gruplanmamış sol dış birleşim örneklerini görmek için projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Bir bileşik anahtarı kullanarak bir katılma işlemi  
 Kullanabileceğiniz `And` anahtar sözcüğü bir `Join` veya `Group Join` eşleştirme yapılırken kullanılacak birden çok anahtar alanları tanımlamak için yan tümcesi birleştirilen koleksiyonlardan değerleri. `And` Anahtar sözcüğü belirtir belirtilen tüm anahtar alanları öğeleri katılması için aynı olmalıdır.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Bir bileşik anahtarı kullanarak bir katılma işlemi için  
  
1. Aşağıdaki kodu ekleyin `Module1` bir bileşik anahtarı kullanan bir birleşim örneklerini görmek için projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Kodu çalıştırma  
  
#### <a name="to-add-code-to-run-the-examples"></a>Örnekleri çalıştırmak için kod eklemek için  
  
1. Değiştirin `Sub Main` içinde `Module1` bu konudaki örnek çalıştırmak için aşağıdaki kodu projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Örnekleri çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From Yan Tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ (C#) ile veri dönüştürmeler](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
