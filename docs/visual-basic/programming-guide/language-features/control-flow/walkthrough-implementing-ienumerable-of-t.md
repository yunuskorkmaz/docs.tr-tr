---
title: IEnumerable uygulama
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f1f0036c38299f2392f8c8705e67b7bb6b7db068
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058644"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>İzlenecek yol: Visual Basic'de IEnumerable(Of T) Uygulama

<xref:System.Collections.Generic.IEnumerable%601>Arabirim, tek seferde bir öğe bir dizi değer döndürebilen sınıflar tarafından uygulanır. Verileri bir kerede bir öğe döndürmesinin avantajı, verilerle çalışmak için tüm veri kümesini belleğe yüklemeniz gerekmez. Verilerden tek bir öğe yüklemek için yeterli bellek kullanmanız gerekir. Arabirimi uygulayan sınıflar, `IEnumerable(T)` `For Each` döngüler veya LINQ sorguları ile kullanılabilir.  
  
 Örneğin, büyük bir metin dosyasını okuması ve her satırı belirli arama ölçütleriyle eşleşen dosyadan döndürmesi gereken bir uygulamayı düşünün. Uygulama, dosyadan belirtilen ölçütlerle eşleşen satırları döndürmek için bir LINQ sorgusu kullanır. Bir LINQ sorgusu kullanarak dosyanın içeriğini sorgulamak için, uygulama dosyanın içeriğini bir diziye veya koleksiyona yükleyebilir. Ancak, tüm dosyanın bir diziye veya koleksiyona yüklenmesi gerekenden çok daha fazla bellek tüketir. LINQ sorgusu bunun yerine, yalnızca arama ölçütleriyle eşleşen değerleri döndürerek sıralanabilir bir sınıf kullanarak dosya içeriğini sorgulayabilir. Yalnızca birkaç eşleşen değeri döndüren sorgular çok daha az bellek tüketir.  
  
 <xref:System.Collections.Generic.IEnumerable%601>Kaynak verileri sıralanabilir veriler olarak göstermek için arabirimi uygulayan bir sınıf oluşturabilirsiniz. Arabirimi uygulayan sınıfınız, `IEnumerable(T)` <xref:System.Collections.Generic.IEnumerator%601> kaynak verilerde yinelemek için arabirimi uygulayan başka bir sınıf gerektirir. Bu iki sınıf, veri öğelerini sırayla belirli bir tür olarak döndürmelerini sağlar.  
  
 Bu kılavuzda, arabirimi uygulayan bir sınıf `IEnumerable(Of String)` ve tek seferde bir `IEnumerator(Of String)` metin dosyasını okumak için arabirimi uygulayan bir sınıf oluşturacaksınız.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Sıralanabilir sınıf oluşturma  
  
**Sıralanabilir sınıf projesi oluşturma**

1. Visual Basic, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

1. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **sınıf kitaplığı** ' nı seçin. **Ad** kutusuna yazın `StreamReaderEnumerable` ve ardından **Tamam**' a tıklayın. Yeni proje görüntülenir.

1. **Çözüm Gezgini**, Class1. vb dosyasına sağ tıklayın ve **Yeniden Adlandır**' a tıklayın. Dosyayı olarak yeniden adlandırın `StreamReaderEnumerable.vb` ve ENTER 'a basın. Dosyanın yeniden adlandırılması de sınıfı olarak yeniden adlandırılacaktır `StreamReaderEnumerable` . Bu sınıf, arabirimini uygular `IEnumerable(Of String)` .

1. Streamreadersıralanabilir projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Sınıf** şablonunu seçin. **Ad** kutusuna yazın `StreamReaderEnumerator.vb` ve **Tamam**' ı tıklatın.

 Bu projedeki ilk sınıf, sıralanabilir sınıftır ve `IEnumerable(Of String)` arabirimini uygular. Bu genel arabirim arabirimini uygular <xref:System.Collections.IEnumerable> ve bu sınıfın tüketicilerinin olarak yazılan değerlere erişebilmesini güvence altına alır `String` .  
  
**IEnumerable uygulamak için kodu ekleyin**

1. Streamreadersıralanabilir. vb dosyasını açın.

2. Sonraki satıra `Public Class StreamReaderEnumerable` aşağıdakini yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic, sınıfı otomatik olarak arabirimin gerektirdiği üyelerle doldurur `IEnumerable(Of String)` .
  
3. Bu sıralanabilir sınıf, bir metin dosyasındaki satırları tek seferde bir satır okur. Bir dosya yolunu giriş parametresi olarak alan bir ortak oluşturucuyu açığa çıkarmak için aşağıdaki kodu sınıfına ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Arabirim yöntemi uygulamanız, <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `IEnumerable(Of String)` sınıfının yeni bir örneğini döndürür `StreamReaderEnumerator` . `GetEnumerator` `IEnumerable` `Private` Yalnızca arabirimin üyelerini kullanıma sunabileceğiniz için arabirim yönteminin uygulanması yapılabilir `IEnumerable(Of String)` . Yöntemler için Visual Basic oluşturulan kodu `GetEnumerator` aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**IEnumerator uygulamak için kodu ekleyin**

1. StreamReaderEnumerator. vb dosyasını açın.

2. Sonraki satıra `Public Class StreamReaderEnumerator` aşağıdakini yazın ve ENTER tuşuna basın.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic, sınıfı otomatik olarak arabirimin gerektirdiği üyelerle doldurur `IEnumerator(Of String)` .

3. Numaralandırıcı sınıfı metin dosyasını açar ve dosyadaki satırları okumak için g/ç dosyasını gerçekleştirir. Bir dosya yolunu giriş parametresi olarak alan ve metin dosyasını okumak için açan bir ortak oluşturucuyu açığa çıkarmak için sınıfına aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`Hem hem de arabirimlerinin özellikleri `IEnumerator(Of String)` , `IEnumerator` metin dosyasındaki geçerli öğeyi bir olarak döndürür `String` . `Current` `IEnumerator` `Private` Yalnızca arabirimin üyelerini kullanıma sunabileceğiniz için arabirimin özelliğinin uygulanması yapılabilir `IEnumerator(Of String)` . Özellikler için Visual Basic oluşturulan kodu `Current` aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext` `IEnumerator` Arabirim yöntemi metin dosyasındaki bir sonraki öğeye gider ve özelliği tarafından döndürülen değeri günceller `Current` . Okunacak başka öğe yoksa `MoveNext` Yöntem döner `False` ; Aksi takdirde `MoveNext` Yöntem döndürülür `True` . `MoveNext` yöntemine aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`Arabirim yöntemi, `IEnumerator` yineleyiciyi metin dosyasının başlangıcına işaret etmek için yönlendirir ve geçerli öğe değerini temizler. `Reset` yöntemine aşağıdaki kodu ekleyin.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`Arabirim yöntemi, `IEnumerator` Yineleyici yok etmeden önce tüm yönetilmeyen kaynakların serbest bırakılacağını garanti eder. Nesne tarafından kullanılan dosya tanıtıcısı `StreamReader` yönetilmeyen bir kaynaktır ve yineleyici örneği yok edileceği için kapatılmalıdır. Yöntemi için Visual Basic oluşturulan kodu `Dispose` aşağıdaki kodla değiştirin.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Örnek Yineleyici kullanma

 Kodunuzda `IEnumerable` , bir `For Next` döngü veya LINQ sorgusu gibi, uygulayan bir nesne gerektiren denetim yapıları ile birlikte sıralanabilir bir sınıf kullanabilirsiniz. Aşağıdaki örnekte, `StreamReaderEnumerable` BIR LINQ sorgusunda gösterilmektedir.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../linq/introduction-to-linq.md)
- [Denetim akışı](index.md)
- [Döngü Yapıları](loop-structures.md)
- [For Each...Next Deyimi](../../../language-reference/statements/for-each-next-statement.md)
