---
title: Visual Basic'de IEnumerable arabirimini uygulama
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4645153f9c830bc96b7ec55367f46f09098eb78d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>İzlenecek yol: Visual Basic'de IEnumerable(Of T) Uygulama
<xref:System.Collections.Generic.IEnumerable%601> Arabirimi değerleri bir öğe dizisi aynı anda geri dönebilirsiniz sınıflar tarafından gerçekleştirilir. Bir seferde bir öğe ile çalışması belleğe eksiksiz veri yüklemek gerekmez veri döndüren avantajı. Yalnızca tek bir öğe verileri yüklemek için yeterli bellek kullanmak zorunda. Sınıfları uygulayan `IEnumerable(T)` arabirimi ile kullanılabilir `For Each` döngüler veya LINQ sorgularını.  
  
 Örneğin, gereken büyük metin dosyası okuma ve her satırın belirli arama ölçütleriyle eşleşen dosyasından bir uygulama göz önünde bulundurun. Uygulama, belirtilen ölçütlerle eşleşen dosyasından satırlar döndürülecek LINQ sorgusu kullanır. Dosya içeriğini bir LINQ Sorgu kullanarak sorgulamak için uygulama dosyasının içeriğini bir dizi veya bir koleksiyon yükleyemedik. Ancak, bir dizi veya koleksiyon dosyanın tamamını yüklenirken gerekenden çok daha fazla bellek kullanılmasına neden olur. LINQ sorgusu, bunun yerine arama ölçütleriyle eşleşen değerler döndüren bir numaralandırılabilir sınıfını kullanarak dosya içeriklerini sorgulayabilir. Yalnızca birkaç döndüren sorgular eşleşen değerleri çok daha az bellek kullanmak.  
  
 Uygulayan bir sınıf oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> kaynak veri numaralandırılabilir veri olarak kullanıma sunmak için arabirim. Uygulayan sınıfınız `IEnumerable(T)` arabirimi uygulayan başka bir sınıf gerektirecektir <xref:System.Collections.Generic.IEnumerator%601> kaynak verilerine yinelemek için arabirim. Bu iki sınıf veri öğeleri belirli bir tür olarak sıralı olarak döndürmek etkinleştirin.  
  
 Bu kılavuzda, uygulayan bir sınıf oluşturacak `IEnumerable(Of String)` arabirimi ve uygulayan bir sınıf `IEnumerator(Of String)` aynı anda metin dosyası tek bir çizgi okumak için arabirim.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Numaralandırılabilir sınıfı oluşturma  
  
|Numaralandırılabilir sınıfı projesi oluşturmak için|  
|---|  
|1.  Visual Basic'te üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.<br />2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `StreamReaderEnumerable`ve ardından **Tamam**. Yeni Proje görüntülenir.<br />3.  İçinde **Çözüm Gezgini**, Class1.vb'ye dosyasını sağ tıklatın ve **yeniden adlandırma**. Dosyayı Yeniden Adlandır `StreamReaderEnumerable.vb` ve ENTER tuşuna basın. Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `StreamReaderEnumerable`. Bu sınıf gerçekleştireceksiniz `IEnumerable(Of String)` arabirimi.<br />4.  StreamReaderEnumerable projeye sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**. Seçin **sınıfı** şablonu. İçinde **adı** kutusuna `StreamReaderEnumerator.vb` tıklatıp **Tamam**.|  
  
 İlk sınıf bu projede numaralandırılabilir sınıftır ve gerçekleştireceksiniz `IEnumerable(Of String)` arabirimi. Bu genel arabirimini uygulayan <xref:System.Collections.IEnumerable> arabirimi ve bu sınıfın tüketicileri olarak yazılan değerleri erişebilirsiniz garanti `String`.  
  
|IEnumerable uygulamak üzere kod eklemek için|  
|---|  
|1.  StreamReaderEnumerable.vb dosyasını açın.<br />2.  Sonra satırındaki `Public Class StreamReaderEnumerable`, aşağıdaki komutu yazın ve ENTER tuşuna basın.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     Visual Basic sınıfı tarafından gerekli üyeleri ile otomatik olarak doldurur `IEnumerable(Of String)` arabirimi.<br />3.  Bu numaralandırılabilir sınıf aynı anda bir metin dosyası bir satırından satırları okuyun. Bir dosya yolu giriş parametresi olarak alan bir public oluşturucuya kullanıma sunmak için sınıfa aşağıdaki kodu ekleyin.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Uygulamanıza <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi `IEnumerable(Of String)` arabirimi yeni bir örneğini döndürür `StreamReaderEnumerator` sınıfı. Uygulaması `GetEnumerator` yöntemi `IEnumerable` arabirimi yapılabilir `Private`, yalnızca üyeleri kullanıma sunmak olduğundan `IEnumerable(Of String)` arabirimi. Visual Basic için oluşturulan kodu değiştirin `GetEnumerator` aşağıdaki kodla yöntemleri.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|Uygulamak üzere kod eklemek için|  
|---|  
|1.  StreamReaderEnumerator.vb dosyasını açın.<br />2.  Sonra satırındaki `Public Class StreamReaderEnumerator`, aşağıdaki komutu yazın ve ENTER tuşuna basın.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     Visual Basic sınıfı tarafından gerekli üyeleri ile otomatik olarak doldurur `IEnumerator(Of String)` arabirimi.<br />3.  Numaralandırıcı sınıfı metin dosyası açılır ve dosyanın g/ç satırları dosyasını okumaya gerçekleştirir. Metin dosyası okuma için'ni açın ve bir dosya yolu giriş parametresi olarak alan bir public oluşturucuya kullanıma sunmak için sınıfa aşağıdaki kodu ekleyin.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  `Current` Özellikleri her ikisi için de `IEnumerator(Of String)` ve `IEnumerator` arabirimleri metin dosyasından geçerli öğeye dönmesini bir `String`. Uygulaması `Current` özelliği `IEnumerator` arabirimi yapılabilir `Private`, yalnızca üyeleri kullanıma sunmak olduğundan `IEnumerator(Of String)` arabirimi. Visual Basic için oluşturulan kodu değiştirin `Current` aşağıdaki kodla özellikleri.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  `MoveNext` Yöntemi `IEnumerator` arabirimi metin dosyasındaki bir sonraki öğeye gider ve tarafından döndürülen değer güncelleştirmeleri `Current` özelliği. Okumak için daha fazla öğe varsa `MoveNext` yöntemi döndürür `False`; Aksi halde `MoveNext` yöntemi döndürür `True`. Aşağıdaki kodu ekleyin `MoveNext` yöntemi.<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  `Reset` Yöntemi `IEnumerator` arabirimi metin dosyasının başlangıcına işaret edecek şekilde yineleyici yönlendirir ve geçerli öğe değeri temizler. Aşağıdaki kodu ekleyin `Reset` yöntemi.<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  `Dispose` Yöntemi `IEnumerator` arabirimi garanti yineleyici yok önce tüm yönetilmeyen kaynakları serbest bırakılır. Tarafından kullanılan dosya tanıtıcısı `StreamReader` nesne yönetilmeyen bir kaynaktır ve yineleyici örneği yok önce kapatılması gerekir. Visual Basic için oluşturulan kodu değiştirin `Dispose` aşağıdaki kod ile yöntemi.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>Örnek yineleyici kullanma  
 Numaralandırılabilir bir sınıf kodunuzda uygulayan bir nesneye gerekli denetim yapıları ile birlikte kullanabileceğiniz `IEnumerable`, gibi bir `For Next` döngü ya da bir LINQ Sorgu. Aşağıdaki örnekte gösterildiği `StreamReaderEnumerable` LINQ Sorgu.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next Deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
