---
title: TümevarLanabilir Uygulama
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266917"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>İzlenecek yol: Visual Basic'de IEnumerable(Of T) Uygulama
Arabirim, <xref:System.Collections.Generic.IEnumerable%601> bir defada bir öğe olan değerler dizisini döndürebilen sınıflar tarafından uygulanır. Verileri bir seferde bir öğe döndürmenin avantajı, onunla çalışmak için tüm veri kümesini belleğe yüklemeniz gerekmemesidir. Verilerden tek bir öğeyi yüklemek için yalnızca yeterli bellek kullanmanız gerekir. `IEnumerable(T)` Arabirimi uygulayan sınıflar döngüler `For Each` veya LINQ sorguları ile kullanılabilir.  
  
 Örneğin, büyük bir metin dosyasını okuması ve belirli arama ölçütleri ile eşleşen dosyadan her satırı döndürmesi gereken bir uygulama düşünün. Uygulama, belirtilen ölçütlere uyan dosyadan satırları döndürmek için bir LINQ sorgusu kullanır. Linq sorgusu kullanarak dosyanın içeriğini sorgulamak için, uygulama dosyanın içeriğini bir diziye veya koleksiyona yükleyebilir. Ancak, tüm dosyayı bir diziye veya koleksiyona yüklemek gerekenden çok daha fazla bellek tüketir. LINQ sorgusu bunun yerine, yalnızca arama ölçütleri ile eşleşen değerleri döndürerek, dosya içeriğini yeniden kullanılabilir bir sınıf kullanarak sorgulayabilir. Yalnızca birkaç eşleşen değer döndüren sorgular çok daha az bellek tüketir.  
  
 Kaynak verileri sayısal veriler olarak <xref:System.Collections.Generic.IEnumerable%601> ortaya çıkarmak için arabirimi uygulayan bir sınıf oluşturabilirsiniz. `IEnumerable(T)` Arabirimi uygulayan sınıfınız, kaynak veriler aracılığıyla <xref:System.Collections.Generic.IEnumerator%601> yinelenecek arabirimi uygulayan başka bir sınıf gerektirir. Bu iki sınıf, belirli bir tür olarak sırayla veri öğeleri döndürmenize olanak sağlar.  
  
 Bu gözden geçirme de, `IEnumerable(Of String)` arabirimi uygulayan bir sınıf ve bir `IEnumerator(Of String)` metin dosyasını teker tek satır okumak için arabirimi uygulayan bir sınıf oluşturursunuz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Sayısal Sınıf Oluşturma  
  
**Sayısal sınıf projesini oluşturma**

1. Visual Basic'te **Dosya** menüsünde **Yeni'yi** işaret edin ve **Project'i**tıklatın.

1. Yeni **Proje** iletişim kutusunda, **Proje Türleri** bölmesinde **Windows'un** seçildiğinden emin olun. **Şablonlar** bölmesinde **Sınıf Kitaplığı'nı** seçin. **Ad** kutusuna, `StreamReaderEnumerable`''yı yazın ve sonra **Tamam'ı**tıklatın. Yeni proje görüntülenir.

1. **Çözüm Gezgini'nde**Class1.vb dosyasına sağ tıklayın ve **Yeniden Adlandır'ı**tıklatın. Dosyayı enter `StreamReaderEnumerable.vb` tuşuna yeniden adlandırın ve ENTER tuşuna basın. Dosyayı yeniden adlandırma da sınıfı `StreamReaderEnumerable`' nun adını .'a yeniden adla taslar Bu sınıf `IEnumerable(Of String)` arabirimi uygular.

1. StreamReaderEnumerable projesini sağ tıklatın, **Ekle'ye**işaret edin ve ardından **Yeni Öğe'yi**tıklatın. **Sınıf** şablonu'nu seçin. **Ad** kutusuna Tamam `StreamReaderEnumerator.vb` yazın ve **tıklatın.**

 Bu projede birinci sınıf sayısal sınıf ve `IEnumerable(Of String)` arayüzü uygulayacak. Bu genel arabirim <xref:System.Collections.IEnumerable> arabirimi uygular ve bu sınıfın tüketicilerinin `String`.  
  
**Tümesiyatize uygulamak için kodu ekleyin**

1. StreamReaderEnumerable.vb dosyasını açın.

2. Satırda sonra, `Public Class StreamReaderEnumerable`aşağıdaki leri yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic, sınıfı `IEnumerable(Of String)` arabirim tarafından gerekli olan üyelerle otomatik olarak doldurur.
  
3. Bu sayısal sınıf, bir metin dosyasındaki satırları bir defada bir satır okur. Dosya yolunu giriş parametresi olarak alan bir ortak oluşturucuyu ortaya çıkarmak için sınıfa aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Arabirim <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemini uygulamanız sınıfın yeni bir `StreamReaderEnumerator` örneğini döndürecektir. `IEnumerable(Of String)` Arabirimin `GetEnumerator` yönteminin uygulanması `Private`yapılabilir, çünkü `IEnumerable(Of String)` yalnızca arabirimin üyelerini ortaya çıkarmanız gerekir. `IEnumerable` Visual Basic'in `GetEnumerator` yöntemler için oluşturduğu kodu aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**IEnumerator uygulamak için kodu ekleyin**

1. StreamReaderEnumerator.vb dosyasını açın.

2. Satırda sonra, `Public Class StreamReaderEnumerator`aşağıdaki leri yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic, sınıfı `IEnumerator(Of String)` arabirim tarafından gerekli olan üyelerle otomatik olarak doldurur.

3. Enumerator sınıfı metin dosyasını açar ve dosyadaki satırları okumak için G/Ç dosyasını gerçekleştirir. Bir dosya yolunu giriş parametresi olarak alan bir ortak oluşturucuyu ortaya çıkarmak ve metin dosyasını okumak için açmak için sınıfa aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Hem `Current` arabirimlerin `IEnumerator(Of String)` hem `IEnumerator` de arabirimlerin özellikleri, metin dosyasından geçerli öğeyi bir `String`. Arabirimin `Current` özelliğinin uygulanması `Private`yapılabilir, çünkü `IEnumerator(Of String)` yalnızca arabirimin üyelerini ortaya çıkarmanız gerekir. `IEnumerator` Visual Basic'in `Current` özellikler için oluşturduğu kodu aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. Arabirimin `MoveNext` yöntemi metin dosyasındaki bir sonraki öğeye doğru ilerler ve `Current` özellik tarafından döndürülen değeri güncelleştirir. `IEnumerator` Okunacak başka öğe yoksa, `MoveNext` yöntem `False`döndürür; aksi `MoveNext` takdirde `True`yöntem döndürür. `MoveNext` yöntemine aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `IEnumerator` Arabirimin `Reset` yöntemi, yinelemeyi metin dosyasının başlangıcına işaret etmeye yönlendirir ve geçerli madde değerini temizler. `Reset` yöntemine aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `IEnumerator` Arabirimin yöntemi, `Dispose` yineleyici yok edilmeden önce tüm yönetilmeyen kaynakların serbest bırakılmasını garanti eder. `StreamReader` Nesne tarafından kullanılan dosya işleyicisi yönetilmeyen bir kaynaktır ve yineleyici örneği yok edilmeden önce kapatılması gerekir. Visual Basic'in `Dispose` yöntem için oluşturduğu kodu aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Örnek Yinelemeyi Kullanma

 Döngü veya LINQ sorgusu gibi `IEnumerable` `For Next` bir nesne gerektiren denetim yapıları ile birlikte kodunuzda sayısalsınıf kullanabilirsiniz. Aşağıdaki `StreamReaderEnumerable` örnekte BIR LINQ sorgusunda gösterir.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Kontrol Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
