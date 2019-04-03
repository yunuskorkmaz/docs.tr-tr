---
title: .NET Framework yöntemleri (Visual Basic) kullanarak dosyaları düzenleme
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 2361a42ececbe12b5f61833e5a40607c8215a65d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821068"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>İzlenecek yol: .NET Framework yöntemleri (Visual Basic) kullanarak dosyaları düzenleme
Bu izlenecek yol, açın ve kullanarak bir dosyayı okumak gösterilmiştir <xref:System.IO.StreamReader> sınıfı, bir dosya erişilebilir olmadığını kontrol edin, bir dize örneği ile okuma dosya içindeki arama <xref:System.IO.StreamReader> sınıfı ve kullanarak bir dosyaya yazma <xref:System.IO.StreamWriter> sınıfı.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Uygulama oluşturma  
 Visual Studio'yu başlatın ve proje kullanıcı belirtilen dosyaya yazmak için kullanabileceğiniz bir form oluşturarak başlayın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni proje**.  
  
2.  İçinde **yeni proje** bölmesinde tıklayın **Windows uygulama**.  
  
3.  İçinde **adı** kutusuna `MyDiary` tıklatıp **Tamam**.  
  
     Visual Studio projeyi ekler **Çözüm Gezgini**ve **Windows Form Tasarımcısı** açılır.  
  
4.  Denetimler aşağıdaki tabloda forma ekleyin ve karşılık gelen özelliklerini ayarlayın.  
  
|**Nesne**|**Özellikler**|**Değer**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Submit`<br /><br /> **Giriş başvurunuzu**|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Clear`<br /><br /> **Girişi Temizle**|  
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Çok satırlı**|`Entry`<br /><br /> **Lütfen bir şey girin.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Dosyaya yazma  
 Uygulama yoluyla bir dosyaya yazma olanağı eklemek için <xref:System.IO.StreamWriter> sınıfı. <xref:System.IO.StreamWriter> belirli bir kodlamaya, karakter çıkışını ise tasarlanmıştır <xref:System.IO.Stream> sınıfı giriş ve çıkış baytı için tasarlanmıştır. Kullanım <xref:System.IO.StreamWriter> satır bilgi standart bir metin dosyasına yazma. Daha fazla bilgi için <xref:System.IO.StreamWriter> sınıfı <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Yazma işlevselliği eklemek için  
  
1.  Gelen **görünümü** menüsünde seçin **kod** Kod Düzenleyicisi'ni açın.  
  
2.  Uygulama başvurduğundan <xref:System.IO> ad alanı, kodunuzu çok başında aşağıdaki deyimleri ekleyin, formu için sınıf bildiriminden önce başlar `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]  
  
     Dosyaya yazmadan önce bir örneğini oluşturmanız gerekir bir <xref:System.IO.StreamWriter> sınıfı.  
  
3.  Gelen **görünümü** menüsünde seçin **Tasarımcısı** dönmek için **Windows Form Tasarımcısı**. Çift `Submit` oluşturmak için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi, düğmenin ve ardından aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]  
  
> [!NOTE]
>  Visual Studio tümleşik geliştirme ortamı (IDE), Kod Düzenleyicisi'ne dönmek ve burada kodu buraya eklemelisiniz içinde olay işleyicisi ekleme noktasını yerleştirin.  
  
1.  Dosyaya yazmak için kullanın <xref:System.IO.StreamWriter.Write%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı. Hemen sonra aşağıdaki kodu ekleyin `Dim fw As StreamWriter`. Dosya bulunamazsa, zaten yoksa, oluşturulur çünkü bir özel durum oluşturulur, endişelenmeniz gerekmez.  
  
     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]  
  
2.  Hemen sonra aşağıdaki kodu ekleyerek kullanıcı boş bir girdiyi gönderemiyor emin `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]  
  
3.  Bu bir günlük olduğundan, kullanıcının her giriş için bir tarih atamak isteyebilirsiniz. Sonra aşağıdaki kodu ekleyin `fw = New StreamWriter("C:\MyDiary.txt", True)` değişkenini ayarlamak üzere `Today` geçerli tarih.  
  
     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]  
  
4.  Son olarak, temizlemek için kod ekleme <xref:System.Windows.Forms.TextBox>. Aşağıdaki kodu ekleyin `Clear` düğmenin <xref:System.Windows.Forms.Control.Click> olay.  
  
     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]  
  
## <a name="adding-display-features-to-the-diary"></a>Görüntü özellikleri için günlük ekleme  
 Bu bölümde, en son giriş görüntüleyen özellik ekleme `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Ayrıca bir <xref:System.Windows.Forms.ComboBox> girdilerin görüntüleyen ve kendisinden kullanıcı görüntülemek için bir giriş seçebilirsiniz `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Örneği <xref:System.IO.StreamReader> sınıfı okumalardan `MyDiary.txt`. Gibi <xref:System.IO.StreamWriter> sınıfı <xref:System.IO.StreamReader> metin dosyalarını kullanması için tasarlanmıştır.  
  
 Bu bölümde örnekler için denetimleri aşağıdaki tabloda forma eklemek ve özelliklerine karşılık gelen değerlerini ayarlayın.  
  
|Denetim|Özellikler|Değerler|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Görünür**<br /><br /> **Boyutu**<br /><br /> **Çok satırlı**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Display`<br /><br /> **Görüntüleme**|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`GetEntries`<br /><br /> **Girişlerini alma**|  
|<xref:System.Windows.Forms.ComboBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`PickEntries`<br /><br /> **Bir giriş seçin**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>Birleşik giriş kutusunu doldurmak için  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> Üzerinde bir kullanıcının gönderdiğini her girdi, kullanıcının belirli bir tarihten itibaren bir giriş seçebilmeniz tarihleri görüntülemek için kullanılır. Oluşturma bir <xref:System.Windows.Forms.Control.Click> olay işleyicisine `GetEntries` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]  
  
2.  Kodunuzu test etmek için uygulamayı derleyin ve ardından F5 tuşuna basarak **Girişleri Al**. Aşağı açılan oku tıklatın <xref:System.Windows.Forms.ComboBox> giriş tarihleri görüntülemek için.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Seçin ve girişler görüntülemek için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `Display` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]  
  
2.  Kodunuzu test etmek için uygulamayı derlemek üzere F5 tuşuna basın ve sonra bir giriş gönderin. Tıklayın **Girişleri Al**, bir giriş seçin <xref:System.Windows.Forms.ComboBox>ve ardından **görünen**. Seçili girişi içeriğini görünür `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Girişleri değiştirmek veya silmek kullanıcıları etkinleştirme  
 Son olarak, bir giriş kullanarak değiştirmek veya silmek için kullanıcıların ek işlevsellik sağlar içerebilir `DeleteEntry` ve `EditEntry` düğmeleri. Bir giriş görüntülenen sürece her iki düğme devre dışı kalır.  
  
 Denetimler aşağıdaki tabloda forma ekleyin ve karşılık gelen özelliklerini ayarlayın.  
  
|Denetim|Özellikler|Değerler|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`DeleteEntry`<br /><br /> **Girişi Sil**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`EditEntry`<br /><br /> **Girişi düzenlemek**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`SubmitEdit`<br /><br /> **Düzenleme gönderin**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Silme ve girişleri değiştirilmesini etkinleştirmek için  
  
1.  Aşağıdaki kodu ekleyin `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olay, sonra `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]  
  
2.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `DeleteEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]  
  
3.  Bir kullanıcı bir giriş görüntülediğinde `EditEntry` düğmesi hale etkin. Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olayı `Display` sonra düğme `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]  
  
4.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `EditEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]  
  
5.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisi `SubmitEdit` düğmesine tıklayın ve aşağıdaki kodu ekleyin  
  
     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]  
  
 Kodunuzu test etmek için uygulamayı derlemek üzere F5 tuşuna basın. Tıklayın **Girişleri Al**bir girişi seçin ve ardından **görünen**. Giriş belirir `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Tıklayın **Düzenle giriş**. Giriş belirir `Entry` <xref:System.Windows.Forms.TextBox>. Girişi düzenlemek `Entry` <xref:System.Windows.Forms.TextBox> tıklatıp **gönderme Düzenle**. Açık `MyDiary.txt` düzeltmenizi onaylamak için dosya. Artık bir girişi seçin ve tıklayın **girdiyi Sil**. Zaman <xref:System.Windows.Forms.MessageBox> onay istekleri tıklayın **Tamam**. Uygulamayı kapatın ve açın `MyDiary.txt` silme işlemini onaylamak için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [İzlenecek Yollar](../../../../visual-basic/walkthroughs.md)
