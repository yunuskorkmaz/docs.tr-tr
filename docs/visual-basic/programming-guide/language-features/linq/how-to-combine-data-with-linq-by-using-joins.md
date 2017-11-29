---
title: "Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Nasıl yapılır: Birleştirmeleri Kullanarak Verileri LINQ İle Birleştirme (Visual Basic)
Visual Basic sağlar `Join` ve `Group Join` sorgu yan tümceleri, koleksiyonları arasında ortak değerlere göre birden fazla koleksiyonun içeriğini birleştirmenize olanak sağlamak için. Bu değerler olarak da bilinir *anahtar* değerleri. Geliştiriciler ilişkisel veritabanı kavramlarını algılayacağı `Join` olarak INNER JOIN yan tümcesi ve `Group Join` olarak, etkili bir şekilde bir LEFT OUTER JOIN yan tümcesi.  
  
 Bu konudaki örnekler kullanarak veri birleştirme için birkaç yol göstermek `Join` ve `Group Join` sorgu yan tümceleri.  
  
## <a name="create-a-project-and-add-sample-data"></a>Bir proje oluşturma ve örnek veri ekleme  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Örnek veriler ve türlerini içeren bir proje oluşturmak için  
  
1.  Bu konudaki örnekler çalıştırmak için Visual Studio'yu açın ve yeni bir Visual Basic konsol uygulama projesi ekleyin. Visual Basic tarafından oluşturulan Module1.vb dosyasını çift tıklatın.  
  
2.  Bu konuda kullanım örnekleri `Person` ve `Pet` türleri ve aşağıdaki kod örneğinde verileri. Bu kod varsayılan kopyalama `Module1` Visual Basic tarafından oluşturulan modülü.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>JOIN yan tümcesi kullanarak bir iç birleştirme gerçekleştirme  
 INNER JOIN iki koleksiyon verileri birleştirir. Kendisi için belirtilen anahtar değerleriyle eşleşen öğeleri dahil edilir. Eşleşen bir öğe diğer koleksiyonunda yok ya da koleksiyon öğelerinden hariç tutulur.  
  
 Visual Basic'te LINQ bir iç birleştirme gerçekleştirmek için iki seçenek sağlar: dolaylı bir birleşim ve açık bir birleştirme.  
  
 Dolaylı bir birleşim birleştirilecek olan koleksiyonları belirtir bir `From` yan tümcesi ve eşleşen anahtar alanları tanımlayan bir `Where` yan tümcesi. Visual Basic, belirtilen anahtar alanlara göre iki koleksiyon örtük olarak birleştirir.  
  
 Açık bir birleşim kullanarak belirtebilirsiniz `Join` birleştirme kullanmak için hangi anahtar alanlar hakkında belirli olmasını istediğiniz zaman yan tümcesi. Bu durumda, bir `Where` yan tümcesi hala sorgu sonuçlarını filtrelemek için kullanılabilir.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>INNER JOIN JOIN yan tümcesi kullanarak gerçekleştirmek için  
  
1.  Aşağıdaki kodu ekleyin `Module1` iki örtük ve açık iç birleşim örnekleri görmek için projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group Join tümcesi kullanarak bir sol dış birleşim gerçekleştirme  
 Bir sol dış birleştirme sol taraftaki koleksiyondaki tüm öğeleri birleştirme ve yalnızca eşleşen değerleri katılma sağ taraftaki koleksiyonundan içerir. Eşleşen bir öğe sol taraftaki koleksiyonunda bulunmayan tüm öğeleri katılma sağ taraftaki koleksiyonundan gelen sorgu sonucu hariç tutulur.  
  
 `Group Join` Yan tümcesi gerçekleştirir, uygulamada LEFT OUTER JOIN. Ne genellikle bir LEFT OUTER JOIN bilinir ve ne arasındaki farkı `Group Join` yan tümcesi döndürür da `Group Join` birleştirme sol taraftaki koleksiyondaki her öğe için sağ taraftaki koleksiyonundan yan tümcesi grupları sonuçları. İlişkisel bir veritabanında, her iki koleksiyon birleştirme eşleşen öğeleri, sorgudaki her öğe neden bir gruplanmamış sonucunu içerir bir LEFT OUTER JOIN döndürür. Bu durumda, birleştirmenin sol taraftaki koleksiyonundan öğeleri sağ taraftaki koleksiyonundan eşleşen her öğe için yinelenir. Bir sonraki yordamı tamamladıktan sonra bu nasıl göründüğünü görürsünüz.  
  
 Sonuçları almak bir `Group Join` sorgu her gruplandırılmış sorgu sonucu için bir öğe döndürülecek sorgunuzu genişletme tarafından gruplanmamış bir sonucu olarak. Bunu başarmak için üzerinde sorgu olun sahip `DefaultIfEmpty` gruplandırılmış koleksiyonunun yöntemi. Bu, sağ taraftaki koleksiyonundan eşleşen hiçbir sonuç olsa bile birleştirmenin sol taraftaki koleksiyonundan öğeleri hala sorgu sonucunda içerdiği sağlar. Sorgunuz katılma sağ taraftaki koleksiyonundan eşleşen hiçbir değer bulunduğunda bir varsayılan sonuç değeri sağlamak için kod ekleyebilirsiniz.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Left Outer JOIN Grup JOIN yan tümcesi kullanarak gerçekleştirmek için  
  
1.  Aşağıdaki kodu ekleyin `Module1` gruplandırılmış bir sol dış birleştirme ve gruplanmamış sol dış birleşim örnekleri görmek için projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Bileşik bir anahtar kullanarak bir birleştirme gerçekleştirme  
 Kullanabileceğiniz `And` in anahtar sözcüğü bir `Join` veya `Group Join` eşleştirme yapılırken kullanılacak birden çok anahtar alanları tanımlamak için yan tümceyi birleştirilen koleksiyonlarından değerleri. `And` Anahtar sözcüğü belirtir belirtilen tüm anahtar alanları için birleştirilecek öğeleri eşleşmesi gerekir.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Bileşik bir anahtar kullanarak bir birleştirme gerçekleştirme  
  
1.  Aşağıdaki kodu ekleyin `Module1` bileşik bir anahtar kullanan bir birleşim örnekleri görmek için projenizdeki modülü.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Kodu çalıştırma  
  
#### <a name="to-add-code-to-run-the-examples"></a>Örneklerini çalıştırmak üzere kod eklemek için  
  
1.  Değiştir `Sub Main` içinde `Module1` bu konudaki örnekler çalıştırmak için aşağıdaki kod projenizle modülünde.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Örnekleri çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Join tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Burada yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Sorguları](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ (C#) ile veri dönüştürmeler](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
