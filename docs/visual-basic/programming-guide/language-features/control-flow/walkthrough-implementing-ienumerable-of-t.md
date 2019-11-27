---
title: IEnumerable uygulama
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f40fcf7e0724addc478b261dcd36d09e1d8a751a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333695"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>İzlenecek yol: Visual Basic'de IEnumerable(Of T) Uygulama
<xref:System.Collections.Generic.IEnumerable%601> arabirimi, tek seferde bir öğe bir dizi değer döndürebilen sınıflar tarafından uygulanır. Verileri bir kerede bir öğe döndürmesinin avantajı, verilerle çalışmak için tüm veri kümesini belleğe yüklemeniz gerekmez. Verilerden tek bir öğe yüklemek için yeterli bellek kullanmanız gerekir. `IEnumerable(T)` arabirimini uygulayan sınıflar, `For Each` döngüleri veya LINQ sorguları ile kullanılabilir.  
  
 Örneğin, büyük bir metin dosyasını okuması ve her satırı belirli arama ölçütleriyle eşleşen dosyadan döndürmesi gereken bir uygulamayı düşünün. Uygulama, dosyadan belirtilen ölçütlerle eşleşen satırları döndürmek için bir LINQ sorgusu kullanır. Bir LINQ sorgusu kullanarak dosyanın içeriğini sorgulamak için, uygulama dosyanın içeriğini bir diziye veya koleksiyona yükleyebilir. Ancak, tüm dosyanın bir diziye veya koleksiyona yüklenmesi gerekenden çok daha fazla bellek tüketir. LINQ sorgusu bunun yerine, yalnızca arama ölçütleriyle eşleşen değerleri döndürerek sıralanabilir bir sınıf kullanarak dosya içeriğini sorgulayabilir. Yalnızca birkaç eşleşen değeri döndüren sorgular çok daha az bellek tüketir.  
  
 Kaynak verileri sıralanabilir veri olarak göstermek için <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan bir sınıf oluşturabilirsiniz. `IEnumerable(T)` arabirimini uygulayan sınıfınız, kaynak verilerde yinelemek için <xref:System.Collections.Generic.IEnumerator%601> arabirimini uygulayan başka bir sınıf gerektirir. Bu iki sınıf, veri öğelerini sırayla belirli bir tür olarak döndürmelerini sağlar.  
  
 Bu kılavuzda, `IEnumerable(Of String)` arabirimini uygulayan bir sınıf ve bir metin dosyasını tek seferde okumak için `IEnumerator(Of String)` arabirimini uygulayan bir sınıf oluşturacaksınız.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Sıralanabilir sınıf oluşturma  
  
**Sıralanabilir sınıf projesi oluşturma**

1. Visual Basic, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

1. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **sınıf kitaplığı** ' nı seçin. **Ad** kutusuna `StreamReaderEnumerable`yazın ve ardından **Tamam**' a tıklayın. Yeni proje görüntülenir.

1. **Çözüm Gezgini**, Class1. vb dosyasına sağ tıklayın ve **Yeniden Adlandır**' a tıklayın. Dosyayı `StreamReaderEnumerable.vb` olarak yeniden adlandırın ve ENTER 'a basın. Dosyanın yeniden adlandırılması de `StreamReaderEnumerable`sınıfı olarak yeniden adlandırılacaktır. Bu sınıf `IEnumerable(Of String)` arabirimini uygular.

1. Streamreadersıralanabilir projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Sınıf** şablonunu seçin. **Ad** kutusuna `StreamReaderEnumerator.vb` yazın ve **Tamam**' a tıklayın.

 Bu projedeki ilk sınıf, sıralanabilir sınıftır ve `IEnumerable(Of String)` arabirimini uygular. Bu genel arabirim <xref:System.Collections.IEnumerable> arabirimini uygular ve bu sınıfın tüketicilerinin `String`olarak yazılmış değerlere erişebilmesini güvence altına alır.  
  
**IEnumerable uygulamak için kodu ekleyin**

1. Streamreadersıralanabilir. vb dosyasını açın.

2. `Public Class StreamReaderEnumerable`sonraki satıra aşağıdakini yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic, sınıfı `IEnumerable(Of String)` arabirimi için gereken üyelere otomatik olarak doldurur.
  
3. Bu sıralanabilir sınıf, bir metin dosyasındaki satırları tek seferde bir satır okur. Bir dosya yolunu giriş parametresi olarak alan bir ortak oluşturucuyu açığa çıkarmak için aşağıdaki kodu sınıfına ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. `IEnumerable(Of String)` arabirimi <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi uygulamanız `StreamReaderEnumerator` sınıfının yeni bir örneğini döndürür. `IEnumerable` arabiriminin `GetEnumerator` yönteminin uygulanması, yalnızca `IEnumerable(Of String)` arabiriminin üyelerini kullanıma sunabileceğiniz `Private`hale getirilebilir. `GetEnumerator` yöntemleri için Visual Basic oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**IEnumerator uygulamak için kodu ekleyin**

1. StreamReaderEnumerator. vb dosyasını açın.

2. `Public Class StreamReaderEnumerator`sonraki satıra aşağıdakini yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic, sınıfı `IEnumerator(Of String)` arabirimi için gereken üyelere otomatik olarak doldurur.

3. Numaralandırıcı sınıfı metin dosyasını açar ve dosyadaki satırları okumak için g/ç dosyasını gerçekleştirir. Bir dosya yolunu giriş parametresi olarak alan ve metin dosyasını okumak için açan bir ortak oluşturucuyu açığa çıkarmak için sınıfına aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. Hem `IEnumerator(Of String)` hem de `IEnumerator` arabirimlerinin `Current` özellikleri, metin dosyasındaki geçerli öğeyi `String`olarak döndürür. `IEnumerator` arabiriminin `Current` özelliğinin uygulanması, yalnızca `IEnumerator(Of String)` arabiriminin üyelerini kullanıma sunabileceğiniz `Private`hale getirilebilir. `Current` özellikleri için Visual Basic oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `IEnumerator` arabiriminin `MoveNext` yöntemi metin dosyasındaki bir sonraki öğeye gider ve `Current` özelliği tarafından döndürülen değeri günceller. Okunacak daha fazla öğe yoksa `MoveNext` yöntemi `False`döndürür; Aksi takdirde `MoveNext` yöntemi `True`döndürür. `MoveNext` yöntemine aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `IEnumerator` arabiriminin `Reset` yöntemi, yineleyiciyi metin dosyasının başlangıcına işaret etmek ve geçerli öğe değerini temizler. `Reset` yöntemine aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `IEnumerator` arabiriminin `Dispose` yöntemi, yineleyici yok etmeden önce tüm yönetilmeyen kaynakların serbest bırakılacağını garanti eder. `StreamReader` nesnesi tarafından kullanılan dosya tanıtıcısı yönetilmeyen bir kaynaktır ve yineleyici örneği yok edileceği için kapatılmalıdır. `Dispose` yöntemi için Visual Basic oluşturulan kodu aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>Örnek Yineleyici kullanma

 Kodunuzda bir `For Next` döngüsü veya bir LINQ sorgusu gibi `IEnumerable`uygulayan bir nesne gerektiren denetim yapıları ile birlikte sıralanabilir bir sınıfı kullanabilirsiniz. Aşağıdaki örnekte `StreamReaderEnumerable` bir LINQ sorgusunda gösterilmektedir.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
