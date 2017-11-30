---
title: ".NET Framework yöntemlerini (Visual Basic) kullanarak dosyaları düzenleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc42dee640271ef84d35ceeb039d98741d296c5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)
Bu izlenecek yol açabilir ve okuyabilir kullanarak bir dosyaya gösterilmiştir <xref:System.IO.StreamReader> sınıfı, bir dosyaya erişim olmadığını denetleyin, bir dize örneği ile okuma dosyasının içinde arama <xref:System.IO.StreamReader> sınıfı ve kullanarak bir dosyaya yazma <xref:System.IO.StreamWriter> sınıfı.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Uygulama oluşturma  
 Başlat [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ve projeyi kullanıcı için belirtilen dosya yazmak için kullanabileceğiniz bir form oluşturarak başlayın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde, select **yeni proje**.  
  
2.  İçinde **yeni proje** bölmesinde tıklatın **Windows uygulaması**.  
  
3.  İçinde **adı** kutusuna `MyDiary` tıklatıp **Tamam**.  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]projeye ekler **Çözüm Gezgini**ve **Windows Form Tasarımcısı** açar.  
  
4.  Denetimleri aşağıdaki tabloda forma ekleme ve bunların özelliklerini karşılık gelen değerler ayarlayın.  
  
|**Nesne**|**Veri Erişimi**|**Değer**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Submit`<br /><br /> **Giriş gönderme**|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Clear`<br /><br /> **Giriş temizleyin**|  
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Çok satırlı**|`Entry`<br /><br /> **Lütfen bir şey girin.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Dosyaya yazma  
 Uygulama yoluyla bir dosyaya yazma özelliği eklemek için kullanın <xref:System.IO.StreamWriter> sınıfı. <xref:System.IO.StreamWriter>karakter çıkışını bir belirli kodlama, ancak için tasarlanmış <xref:System.IO.Stream> sınıfı, giriş ve çıkış bayt için tasarlanmıştır. Kullanım <xref:System.IO.StreamWriter> satır bilgi standart metin dosyasına yazma. Daha fazla bilgi için <xref:System.IO.StreamWriter> sınıfı için bkz: <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Yazma işlevselliği eklemek için  
  
1.  Gelen **Görünüm** menüsünde seçin **kod** Kod Düzenleyicisi'ni açın.  
  
2.  Uygulama başvurduğundan <xref:System.IO> ad alanı, kodunuzun en başından aşağıdaki deyimleri ekleyin, form için sınıf bildirimi önce hangi başlar `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     Dosyaya yazmak için önce bir örneğini oluşturmanız gerekir bir <xref:System.IO.StreamWriter> sınıfı.  
  
3.  Gelen **Görünüm** menüsünde seçin **Tasarımcısı** geri dönmek için **Windows Form Tasarımcısı**. Çift `Submit` oluşturmak için düğmesini bir <xref:System.Windows.Forms.Control.Click> düğmesi için olay işleyicisini ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  Visual Studio tümleşik geliştirme ortamı (IDE) kod düzenleyicisine dönün ve kodu nereye ekleyin olay işleyici içinde ekleme noktasını yerleştirin.  
  
1.  Dosyaya yazmak için <xref:System.IO.StreamWriter.Write%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı. Hemen sonra aşağıdaki kodu ekleyin `Dim fw As StreamWriter`. Dosya bulunamazsa, zaten yoksa, oluşturulur çünkü bir özel durum atılır olduğunu endişelenmeniz gerekmez.  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  Kullanıcı boş bir girdiyi hemen sonra aşağıdaki kodu ekleyerek gönderemiyor emin `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  Bu bir günlük olduğundan, kullanıcının her giriş için bir tarih atamak istediğiniz. Sonra aşağıdaki kodu ekleyin `fw = New StreamWriter("C:\MyDiary.txt", True)` değişken ayarlamak üzere `Today` geçerli tarihi.  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  Son olarak, temizlemek için kod ekleme <xref:System.Windows.Forms.TextBox>. Aşağıdaki kodu ekleyin `Clear` düğmenin <xref:System.Windows.Forms.Control.Click> olay.  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a>Günlük görüntüleme özellik ekleme  
 Bu bölümde, en son giriş görüntüleyen özellik ekleme `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Ayrıca ekleyebileceğiniz bir <xref:System.Windows.Forms.ComboBox> çeşitli girişleri görüntüler ve kullanıcının seçebileceği görüntülemek için bir giriş `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Örneği <xref:System.IO.StreamReader> sınıf okuma `MyDiary.txt`. Gibi <xref:System.IO.StreamWriter> sınıfı, <xref:System.IO.StreamReader> metin dosyalarını kullanılmaya yöneliktir.  
  
 Bu bölümde örnekler için aşağıdaki tabloda formuna denetim eklemek için ve özelliklerini karşılık gelen değerler ayarlayın.  
  
|Denetim|Özellikler|Değerler|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Görünür**<br /><br /> **Boyutu**<br /><br /> **Çok satırlı**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Display`<br /><br /> **Görüntüleme**|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`GetEntries`<br /><br /> **Girişlerini alma**|  
|<xref:System.Windows.Forms.ComboBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`PickEntries`<br /><br /> **Bir giriş seçin**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>Birleşik giriş kutusunu doldurmak için  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> Üzerinde bir kullanıcının gönderdiğini her giriş kullanıcı belirli bir tarihten itibaren bir giriş seçebilmeniz için tarihleri görüntülemek için kullanılır. Oluşturma bir <xref:System.Windows.Forms.Control.Click> olay işleyicisine `GetEntries` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  Kodunuzu test etmek için uygulamayı derleyin ve ardından için F5 tuşuna basın **Girişleri Al**. Aşağı açılan oku tıklatın <xref:System.Windows.Forms.ComboBox> giriş tarihleri görüntülemek için.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Seçin ve girişleri tek tek görüntülemek için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `Display` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  Kodunuzu test etmek için uygulama derlemek için F5 tuşuna basın ve ardından bir giriş göndermek. Tıklatın **Girişleri Al**, bir giriş seçin <xref:System.Windows.Forms.ComboBox>ve ardından **görüntü**. Seçilen girişi içeriğini görünür `DisplayEntry` <xref:System.Windows.Forms.TextBox>.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Silmek veya girişleri değiştirmek kullanıcıları etkinleştirme  
 Son olarak, bir giriş kullanarak değiştirmek veya silmek için kullanıcıların ek işlevsellik sağlar içerebilir `DeleteEntry` ve `EditEntry` düğmeler. Bir giriş görüntülenen sürece her iki düğmeleri devre dışı kalır.  
  
 Denetimleri aşağıdaki tabloda forma ekleme ve bunların özelliklerini karşılık gelen değerler ayarlayın.  
  
|Denetim|Özellikler|Değerler|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`DeleteEntry`<br /><br /> **Giriş silme**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`EditEntry`<br /><br /> **Girişi Düzenle**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkin**|`SubmitEdit`<br /><br /> **Düzen gönderme**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Silme ve girişleri değiştirilmesini etkinleştirmek için  
  
1.  Aşağıdaki kodu ekleyin `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olay, sonra `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `DeleteEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  Bir kullanıcı bir giriş görüntülediğinde `EditEntry` düğmesi etkin hale gelir. Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olayı `Display` sonra düğmesini `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `EditEntry` düğmesine tıklayın ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  Oluşturma bir <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `SubmitEdit` düğmesine tıklayın ve aşağıdaki kodu ekleyin  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 Kodunuzu test etmek için uygulama derlemek için F5 tuşuna basın. Tıklatın **Girişleri Al**bir girişi seçin ve ardından **görüntü**. Giriş belirir `DisplayEntry` <xref:System.Windows.Forms.TextBox>. Tıklatın **Düzenle girişi**. Giriş belirir `Entry` <xref:System.Windows.Forms.TextBox>. Girişi düzenlemek `Entry` <xref:System.Windows.Forms.TextBox> tıklatıp **gönderme Düzenle**. Açık `MyDiary.txt` düzeltmenizi onaylamak için dosya. Şimdi bir girişi seçin ve tıklatın **girişi silmek**. Zaman <xref:System.Windows.Forms.MessageBox> onay istekleri tıklatın **Tamam**. Uygulamayı kapatıp açın `MyDiary.txt` silme işlemini onaylayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [İzlenecek yollar](../../../../visual-basic/walkthroughs.md)
