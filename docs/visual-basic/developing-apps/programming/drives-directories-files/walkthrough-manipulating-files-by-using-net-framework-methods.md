---
title: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme
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
ms.openlocfilehash: 02cdbcc59e8817ff4ec06c2f78f835cad77b10f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333777"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>İzlenecek Yol: .NET Framework Yöntemlerini Kullanarak Dosyaları Düzenleme (Visual Basic)

Bu izlenecek yol, <xref:System.IO.StreamReader> sınıfını kullanarak bir dosyayı nasıl açıp okuyacağınızı, bir dosyaya erişilmekte olup olmadığını kontrol etmek için <xref:System.IO.StreamReader> sınıfının örneğiyle okunan bir dosya içinde bir dizeyi aramak ve <xref:System.IO.StreamWriter> sınıfını kullanarak bir dosyaya yazmak demektir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a>Uygulama oluşturma

Visual Studio 'Yu başlatın ve kullanıcının belirlenen dosyaya yazmak için kullanabileceği bir form oluşturarak projeye başlayın.

### <a name="to-create-the-project"></a>Proje oluşturmak için

1. **Dosya** menüsünde **Yeni proje**' yi seçin.

2. **Yeni proje** bölmesinde **Windows uygulaması**' na tıklayın.

3. **Ad** kutusuna `MyDiary` yazın ve **Tamam**' a tıklayın.

     Visual Studio, projeyi **Çözüm Gezgini**ekler ve **Windows Form Tasarımcısı** açılır.

4. Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|**Nesne**|**Özellikler**|**Değer**|
|---|---|---|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Submit`<br /><br /> **Giriş Gönder**|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Clear`<br /><br /> **Girişi temizle**|
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Çok satırlı**|`Entry`<br /><br /> **Lütfen bir ad girin.**<br /><br /> `False`|

## <a name="writing-to-the-file"></a>Dosyaya yazma

Uygulama aracılığıyla bir dosyaya yazma özelliğini eklemek için <xref:System.IO.StreamWriter> sınıfını kullanın. <xref:System.IO.StreamWriter>, belirli bir kodlamada karakter çıkışı için tasarlanmıştır, ancak <xref:System.IO.Stream> sınıfı bayt girişi ve çıkışı için tasarlanmıştır. Bir standart metin dosyasına bilgi satırları yazmak için <xref:System.IO.StreamWriter> kullanın. <xref:System.IO.StreamWriter> sınıfı hakkında daha fazla bilgi için bkz. <xref:System.IO.StreamWriter>.

### <a name="to-add-writing-functionality"></a>Yazma işlevselliği eklemek için

1. **Görünüm** menüsünde **kod** ' yi seçerek kod düzenleyicisini açın.

2. Uygulama <xref:System.IO> ad alanına başvurduğundan, form için Sınıf bildiriminden önce, `Public Class Form1`başlayan, kodunuzun en başına aşağıdaki deyimlerini ekleyin.

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     Dosyaya yazmadan önce <xref:System.IO.StreamWriter> sınıfının bir örneğini oluşturmanız gerekir.

3. **Görünüm** menüsünden, **Windows Form Tasarımcısı**geri dönmek için **Tasarımcı** ' yı seçin. Düğme için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturmak üzere `Submit` düğmesine çift tıklayın ve ardından aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> Visual Studio tümleşik geliştirme ortamı (IDE), kod düzenleyicisine dönerek ekleme noktasını kodu eklemeniz gereken olay işleyicisine göre konumlandıracaktır.

1. Dosyaya yazmak için <xref:System.IO.StreamWriter> sınıfının <xref:System.IO.StreamWriter.Write%2A> yöntemini kullanın. `Dim fw As StreamWriter`sonra doğrudan aşağıdaki kodu ekleyin. Zaten mevcut değilse oluşturulacak bir özel durumun, dosyanın bulunamaması durumunda oluşturulmadığından endişelenmeniz gerekmez.

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. `Dim ReadString As String`hemen sonra aşağıdaki kodu ekleyerek kullanıcının boş bir giriş gönderebildiğinden emin olun.

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. Bu bir Diary olduğundan, Kullanıcı her girişe bir tarih atamak isteyeceksiniz. `fw = New StreamWriter("C:\MyDiary.txt", True)` sonra `Today` değişkeni geçerli tarihe ayarlamak için aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. Son olarak, <xref:System.Windows.Forms.TextBox>temizlemek için kod ekleyin. `Clear` düğmesinin <xref:System.Windows.Forms.Control.Click> olayına aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a>Diary 'e görüntüleme özellikleri ekleme

Bu bölümde, `DisplayEntry`<xref:System.Windows.Forms.TextBox>en son girişi görüntüleyen bir özellik eklersiniz. Ayrıca, çeşitli girdileri görüntüleyen ve kullanıcının `DisplayEntry`<xref:System.Windows.Forms.TextBox>görüntülenecek girişi seçebileceğiniz bir <xref:System.Windows.Forms.ComboBox> ekleyebilirsiniz. <xref:System.IO.StreamReader> sınıfının bir örneği `MyDiary.txt`okur. <xref:System.IO.StreamWriter> sınıfı gibi, <xref:System.IO.StreamReader> metin dosyalarıyla kullanılmak üzere tasarlanmıştır.

İzlenecek yolun bu bölümü için, aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|Denetim|Özellikler|Değerler|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|**Ad**<br /><br /> **Görüne**<br /><br /> **Boyutla**<br /><br /> **Çok satırlı**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`Display`<br /><br /> **Görüntülenme**|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**|`GetEntries`<br /><br /> **Girişleri Al**|
|<xref:System.Windows.Forms.ComboBox>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`PickEntries`<br /><br /> **Bir giriş seçin**<br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a>Birleşik giriş kutusunu doldurmak için

1. `PickEntries`<xref:System.Windows.Forms.ComboBox>, kullanıcının her girişi gönderdiği tarihleri göstermek için kullanılır, böylece Kullanıcı belirli bir tarihten itibaren bir giriş seçebilir. `GetEntries` düğmesine <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından **Girişleri Al**' a tıklayın. Giriş tarihlerini göstermek için <xref:System.Windows.Forms.ComboBox> açılan oka tıklayın.

### <a name="to-choose-and-display-individual-entries"></a>Tek tek girdileri seçme ve görüntüleme

1. `Display` düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin ve ardından bir giriş gönderebilirsiniz. **Girişleri Al**' a tıklayın, <xref:System.Windows.Forms.ComboBox>bir giriş seçin ve ardından **görüntüle**' ye tıklayın. Seçili girdinin içeriği `DisplayEntry`<xref:System.Windows.Forms.TextBox>görüntülenir.

## <a name="enabling-users-to-delete-or-modify-entries"></a>Kullanıcıların girdileri silmesini veya değiştirmesini sağlama

Son olarak, kullanıcıların `DeleteEntry` ve `EditEntry` düğmelerini kullanarak bir girişi silmesine veya değiştirmesine olanak tanıyan ek işlevler ekleyebilirsiniz. Bir giriş görüntülenmediği takdirde her iki düğme de devre dışı kalır.

Aşağıdaki tablodaki denetimleri forma ekleyin ve özellikleri için karşılık gelen değerleri ayarlayın.

|Denetim|Özellikler|Değerler|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`DeleteEntry`<br /><br /> **Girişi Sil**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`EditEntry`<br /><br /> **Girişi Düzenle**<br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|**Ad**<br /><br /> **Metin**<br /><br /> **Etkinletir**|`SubmitEdit`<br /><br /> **Düzenleme gönder**<br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a>Girişlerin silinmesini ve değiştirilmesini etkinleştirmek için

1. `Display` düğmenin <xref:System.Windows.Forms.Control.Click> olayına, `DisplayEntry.Text = ReadString`sonra aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. `DeleteEntry` düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. Bir Kullanıcı bir girişi görüntülediğinde `EditEntry` düğmesi etkinleştirilir. `DisplayEntry.Text = ReadString`sonra `Display` düğmesinin <xref:System.Windows.Forms.Control.Click> olayına aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. `EditEntry` düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin.

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. `SubmitEdit` düğmesi için <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun ve aşağıdaki kodu ekleyin

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

Kodunuzu test etmek için F5 tuşuna basarak uygulamayı derleyin. **Girişleri Al**' a tıklayın, bir giriş seçin ve ardından **görüntüle**' ye tıklayın. Giriş `DisplayEntry`<xref:System.Windows.Forms.TextBox>görünür. **Girişi Düzenle**' ye tıklayın. Giriş `Entry`<xref:System.Windows.Forms.TextBox>görünür. `Entry`<xref:System.Windows.Forms.TextBox> girişi düzenleyin ve **Düzenle gönder**' e tıklayın. Düzeltinizi onaylamak için `MyDiary.txt` dosyasını açın. Şimdi bir girdi seçip **girişi Sil**' e tıklayın. <xref:System.Windows.Forms.MessageBox> onay istediğinde, **Tamam**' a tıklayın. Uygulamayı kapatın ve silme işlemini onaylamak için `MyDiary.txt` açın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [İzlenecek Yollar](../../../../visual-basic/walkthroughs.md)
