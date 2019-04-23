---
title: Visual Basic'de IEnumerable uygulama
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: b13fd85ae01fd0b6f3c963d87a372add930be99d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302588"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>İzlenecek yol: Visual Basic'te IEnumerable(Of T) uygulama
<xref:System.Collections.Generic.IEnumerable%601> Arabirimi, aynı anda bir öğe değerlerini bir dizi döndüren sınıflar tarafından uygulanır. Aynı anda bir öğe ile çalışmak için eksiksiz veri Seti yüklemek gerekmez veri döndüren avantajı. Yalnızca tek bir öğe verileri yüklemek için yeterli bellek kullanmak zorunda. Uygulayan sınıflar `IEnumerable(T)` arabirimi ile kullanılabilir `For Each` döngüler veya LINQ sorguları.  
  
 Örneğin, büyük bir metin dosyası okuma ve her satırın belirli arama ölçütleri ile eşleşen dosyasından dönüş bir uygulamayı düşünün. Uygulama, belirtilen ölçütlerle eşleşen dosyanın satırlar döndürülecek LINQ sorgusu kullanır. LINQ sorgusu kullanarak dosya içeriğini sorgulamak için uygulama dosyasının içeriğini bir dizi veya koleksiyon yükleyebilir. Ancak, bir dizi veya koleksiyon tüm dosya yüklenirken gerekenden çok daha fazla bellek kullanılmasına neden olur. LINQ sorgusu, bunun yerine arama ölçütleriyle eşleşen değerler döndüren bir numaralandırılabilir sınıfını kullanarak dosya içeriklerini sorgulayabilir. Yalnızca birkaç döndüren sorgular eşleşen değerler çok daha az bellek tüketen.  
  
 Uygulayan bir sınıf oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> kaynak verileri numaralandırılabilir veri olarak kullanıma sunmak için arabirim. Sınıfınızın uyguladığı `IEnumerable(T)` arabirimi uygulayan başka bir sınıf gerektiren <xref:System.Collections.Generic.IEnumerator%601> kaynak veri içerisinde yineleme yapmak için arabirim. Bu iki sınıf veri öğelerini belirli bir tür olarak sıralı olarak döndürülecek etkinleştirin.  
  
 Bu kılavuzda, uygulayan bir sınıf oluşturur `IEnumerable(Of String)` arabirimi ve uygulayan bir sınıf `IEnumerator(Of String)` bir metin dosyası bir satırı okumak için arabirim.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Numaralandırılabilir sınıfı oluşturma  
  
**Numaralandırılabilir sınıf projesi oluşturma**

1. Visual Basic'te üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

1. İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `StreamReaderEnumerable`ve ardından **Tamam**. Yeni Proje görüntülenir.

1. İçinde **Çözüm Gezgini**Class1.vb dosyaya sağ tıklayın ve tıklayın **Yeniden Adlandır**. Dosyayı Yeniden Adlandır `StreamReaderEnumerable.vb` ve ENTER tuşuna basın. Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `StreamReaderEnumerable`. Bu sınıf uygulayacak `IEnumerable(Of String)` arabirimi.

1. StreamReaderEnumerable projeye sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**. Seçin **sınıfı** şablonu. İçinde **adı** kutusuna `StreamReaderEnumerator.vb` tıklatıp **Tamam**.

 Bu projedeki ilk sınıf numaralandırılabilir sınıftır ve uygulayacak `IEnumerable(Of String)` arabirimi. Bu genel arabirimi uygulayan <xref:System.Collections.IEnumerable> arabirimi ve bu sınıf tüketicilerinin olarak yazılan değerleri erişebilirsiniz garantiler `String`.  
  
**IEnumerable uygulamak için kod ekleyin**

1. StreamReaderEnumerable.vb dosyasını açın.

2. Sonra satırında `Public Class StreamReaderEnumerable`, aşağıdaki komutu yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic sınıf tarafından gerekli üyeleri ile otomatik olarak doldurur `IEnumerable(Of String)` arabirimi.
  
3. Numaralandırılabilir bu sınıfı aynı anda bir metin dosyası bir satırından satırları oku. Bir dosya yolu giriş parametresi olarak alan bir Genel oluşturucu kullanıma sunmak için sınıfa aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Uygulamanıza <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi `IEnumerable(Of String)` arabirimi yeni bir örneğini döndürür `StreamReaderEnumerator` sınıfı. Uygulamasını `GetEnumerator` yöntemi `IEnumerable` arabirimi yapılabilir `Private`yalnızca üyelerinin kullanıma sunmak sahip olduğunuz için `IEnumerable(Of String)` arabirimi. Visual Basic için oluşturulan kodu değiştirme `GetEnumerator` aşağıdaki kodla yöntemleri.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**IEnumerator uygulamak için kod ekleyin**

1. StreamReaderEnumerator.vb dosyasını açın.

2. Sonra satırında `Public Class StreamReaderEnumerator`, aşağıdaki komutu yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic sınıf tarafından gerekli üyeleri ile otomatik olarak doldurur `IEnumerator(Of String)` arabirimi.

3. Numaralandırıcı sınıfı metin dosyasını açıp ' % s'dosya g/ç satırları dosyasından okumak için gerçekleştirir. Bir dosya yolu giriş parametresi olarak alan bir Genel oluşturucu kullanımına sunun ve metin dosyası okuma için sınıfa aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current` Özellikleri hem de `IEnumerator(Of String)` ve `IEnumerator` arabirimleri metin dosyasından geçerli öğeyi iade bir `String`. Uygulamasını `Current` özelliği `IEnumerator` arabirimi yapılabilir `Private`yalnızca üyelerinin kullanıma sunmak sahip olduğunuz için `IEnumerator(Of String)` arabirimi. Visual Basic için oluşturulan kodu değiştirme `Current` aşağıdaki kodla özellikleri.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext` Yöntemi `IEnumerator` arabirimi metin dosyasındaki bir sonraki öğeye gider ve tarafından döndürülen değerin güncelleştirmeleri `Current` özelliği. Okumak için daha fazla öğe varsa `MoveNext` yöntemi döndürür `False`; Aksi takdirde `MoveNext` yöntemi döndürür `True`. Aşağıdaki kodu ekleyin `MoveNext` yöntemi.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset` Yöntemi `IEnumerator` arabirimi metin dosyası başlangıcına işaret edecek şekilde yineleyici yönlendirir ve geçerli öğe değerini temizler. Aşağıdaki kodu ekleyin `Reset` yöntemi.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose` Yöntemi `IEnumerator` arabirimi garanti yineleyici edildiğinde önce tüm yönetilmeyen kaynaklar serbest bırakılır. Tarafından kullanılan dosya tanıtıcısı `StreamReader` nesne yönetilmeyen bir kaynağı ve yineleyici örneği yok önce kapatılması gerekir. Visual Basic için oluşturulan kodu değiştirme `Dispose` yöntemini aşağıdaki kod ile.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>Örnek yineleyici kullanma

 Numaralandırılabilir bir sınıf uygulayan bir nesne gerektiren denetim yapıları birlikte kodunuzda kullanabileceğiniz `IEnumerable`, gibi bir `For Next` döngü veya LINQ sorgusu. Aşağıdaki örnekte gösterildiği `StreamReaderEnumerable` bir LINQ Sorgu.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
