---
title: .NET Framework yöntemleri kullanarak dosyaları düzenleme (Visual Basic)
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
ms.openlocfilehash: 0b9a899a579a1a38cee3be7b742fd9f0dfa197fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966042"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>İzlenecek yol: .NET Framework yöntemleri kullanarak dosyaları düzenleme (Visual Basic)
Bu izlenecek yol, <xref:System.IO.StreamReader> sınıfını kullanarak bir dosyayı nasıl açıp okuyacağınızı, bir dosyaya erişilmekte olup olmadığını kontrol etmek için, <xref:System.IO.StreamReader> sınıfın örneğiyle okunan bir dosya içinde bir dizeyi aramak ve <xref:System.IO.StreamWriter> sınıfını kullanarak bir dosyaya yazmak için nasıl kullanılacağını gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a>Uygulama oluşturma  
 Visual Studio 'Yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.  
  
### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1. **Dosya** menüsünde **Yeni proje**' yi seçin.  
  
2. **Yeni proje** bölmesinde **Windows uygulaması**' na tıklayın.  
  
3. **Ad** kutusuna yazın `MyDiary` ve **Tamam**' a tıklayın.  
  
     Visual Studio, projeyi **Çözüm Gezgini**ekler ve **Windows Form Tasarımcısı** açılır.  
  
4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.  
  
|**Nesne**|**Özellikler**|**Değer**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Submit`<br /><br /> **Giriş Gönder**|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Clear`<br /><br /> **Girişi temizle**|  
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Çok satırlı**|`Entry`<br /><br /> **Lütfen bir ad girin.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Dosyaya yazma  
 Uygulama aracılığıyla bir dosyaya yazma yeteneğini eklemek için <xref:System.IO.StreamWriter> sınıfını kullanın. <xref:System.IO.StreamWriter>, belirli bir kodlamada karakter çıkışı için tasarlanmıştır, ancak <xref:System.IO.Stream> Sınıf bayt girişi ve çıkışı için tasarlanmıştır. Standart <xref:System.IO.StreamWriter> metin dosyasına bilgi satırları yazmak için kullanın. <xref:System.IO.StreamWriter> Sınıfı hakkında daha fazla bilgi için bkz <xref:System.IO.StreamWriter>.  
  
### <a name="to-add-writing-functionality"></a>Yazma işlevselliği eklemek için  
  
1. **Görünüm** menüsünde **kod** ' yi seçerek kod düzenleyicisini açın.  
  
2. Uygulama <xref:System.IO> ad alanına başvurduğundan, form için Sınıf bildiriminden önce, ' nin başladığı `Public Class Form1`, kodunuzun en başına aşağıdaki deyimlerini ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]  
  
     Dosyaya yazmadan önce bir <xref:System.IO.StreamWriter> sınıfın örneğini oluşturmanız gerekir.  
  
3. **Görünüm** menüsünden, **Windows Form Tasarımcısı**geri dönmek için **Tasarımcı** ' yı seçin. Düğmeye çift tıklayarak `Submit` düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve ardından aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]  
  
> [!NOTE]
> Visual Studio tümleşik geliştirme ortamı (IDE), kod düzenleyicisine dönerek ekleme noktasını kodu eklemeniz gereken olay işleyicisine göre konumlandıracaktır.  
  
1. Dosyaya yazmak için, <xref:System.IO.StreamWriter.Write%2A> <xref:System.IO.StreamWriter> sınıfının yöntemini kullanın. Hemen sonra `Dim fw As StreamWriter`aşağıdaki kodu ekleyin. Zaten mevcut değilse oluşturulacak bir özel durumun, dosyanın bulunamaması durumunda oluşturulmadığından endişelenmeniz gerekmez.  
  
     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]  
  
2. Kullanıcının aşağıdaki kodu doğrudan `Dim ReadString As String`ekleyerek boş bir giriş gönderebildiğinden emin olun.  
  
     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]  
  
3. Bu bir Diary olduğundan, Kullanıcı her girişe bir tarih atamak isteyeceksiniz. `fw = New StreamWriter("C:\MyDiary.txt", True)` Değişkeni`Today` geçerli tarihe ayarlamak için aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]  
  
4. Son olarak, silmek <xref:System.Windows.Forms.TextBox>için kod ekleyin. `Clear` Düğmenin olayınaaşağıdakikoduekleyin.<xref:System.Windows.Forms.Control.Click>  
  
     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]  
  
## <a name="adding-display-features-to-the-diary"></a>Diary 'e görüntüleme özellikleri ekleme  
 Bu bölümde, içinde `DisplayEntry` <xref:System.Windows.Forms.TextBox>en son girişi görüntüleyen bir özellik eklersiniz. Ayrıca, <xref:System.Windows.Forms.ComboBox> `DisplayEntry`çeşitli girdilerigörüntüleyenvebirkullanıcınıniçindegörüntülenecekgirişiseçebileceğinizbirdeekleyebilirsiniz.<xref:System.Windows.Forms.TextBox> <xref:System.IO.StreamReader> Sınıfının bir örneği öğesinden `MyDiary.txt`okur. Sınıfı gibi, <xref:System.IO.StreamReader> metin dosyalarıyla kullanılmak üzere tasarlanmıştır. <xref:System.IO.StreamWriter>  
  
 İzlenecek yolun bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.  
  
|Denetim|Özellikler|Değerler|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Görüne**<br /><br /> **Boyutla**<br /><br /> **Çok satırlı**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Display`<br /><br /> **Görüntülenme**|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`GetEntries`<br /><br /> **Girişleri Al**|  
|<xref:System.Windows.Forms.ComboBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`PickEntries`<br /><br /> **Bir giriş seçin**<br /><br /> `False`|  
  
### <a name="to-populate-the-combo-box"></a>Birleşik giriş kutusunu doldurmak için  
  
1. `PickEntries` ,<xref:System.Windows.Forms.ComboBox> Kullanıcının her girişi gönderdiği tarihleri göstermek için kullanılır, böylece Kullanıcı belirli bir tarihten itibaren bir giriş seçebilir. `GetEntries` Düğmeye bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]  
  
2. Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından **Girişleri Al**' a tıklayın. Giriş tarihlerini göstermek <xref:System.Windows.Forms.ComboBox> için içindeki açılan oka tıklayın.  
  
### <a name="to-choose-and-display-individual-entries"></a>Tek tek girdileri seçme ve görüntüleme  
  
1. Düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin. `Display`  
  
     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]  
  
2. Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından bir giriş gönderebilirsiniz. **Girişleri Al**' a tıklayın, öğesinden <xref:System.Windows.Forms.ComboBox>bir giriş seçin ve ardından **görüntüle**' ye tıklayın. Seçili girdinin içeriği içinde `DisplayEntry` <xref:System.Windows.Forms.TextBox>görüntülenir.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Kullanıcıların girdileri silmesini veya değiştirmesini sağlama  
 Son olarak, kullanıcıların ve `DeleteEntry` `EditEntry` düğmelerini kullanarak bir girişi silmesine veya değiştirmesine izin vermek için ek işlevler ekleyebilirsiniz. Bir giriş görüntülenmediği takdirde her iki düğme de devre dışı kalır.  
  
 Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.  
  
|Denetim|Özellikler|Değerler|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`DeleteEntry`<br /><br /> **Girişi Sil**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`EditEntry`<br /><br /> **Girişi Düzenle**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`SubmitEdit`<br /><br /> **Düzenleme gönder**<br /><br /> `False`|  
  
### <a name="to-enable-deletion-and-modification-of-entries"></a>Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için  
  
1. Aşağıdaki kodu `Display` <xref:System.Windows.Forms.Control.Click> düğmenin olayına, sonrasında `DisplayEntry.Text = ReadString`ekleyin.  
  
     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]  
  
2. Düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin. `DeleteEntry`  
  
     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]  
  
3. Bir Kullanıcı bir girişi görüntülediğinde, `EditEntry` düğme etkin hale gelir. Sonrasında <xref:System.Windows.Forms.Control.Click> düğmeolayına`Display` aşağıdaki kodu ekleyin. `DisplayEntry.Text = ReadString`  
  
     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]  
  
4. Düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin. `EditEntry`  
  
     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]  
  
5. Düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin `SubmitEdit`  
  
     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]  
  
 Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin. **Girişleri Al**' a tıklayın, bir giriş seçin ve ardından **görüntüle**' ye tıklayın. Giriş öğesinde `DisplayEntry` <xref:System.Windows.Forms.TextBox>görüntülenir. **Girişi Düzenle**' ye tıklayın. Giriş öğesinde `Entry` <xref:System.Windows.Forms.TextBox>görüntülenir. `Entry` İçindeki<xref:System.Windows.Forms.TextBox> girişi düzenleyin ve **düzenleme gönder**' e tıklayın. Düzeltmeyi onaylamak için dosyayı açın. `MyDiary.txt` Şimdi bir girdi seçip **girişi Sil**' e tıklayın. İstek onayı tamamlandığında Tamam ' a tıklayın. <xref:System.Windows.Forms.MessageBox> Uygulamayı kapatın ve silme işlemini `MyDiary.txt` onaylamak için açın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [İzlenecek Yollar](../../../../visual-basic/walkthroughs.md)
