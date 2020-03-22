---
title: 'Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 572463d1f03d768fb133f2dac59b012051f053bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334557"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)

Nesne `My.Computer.FileSystem` a ve <xref:System.IO.TextReader> a'yı <xref:System.IO.TextWriter>açmak için yöntemler sağlar. Bu `OpenTextFileWriter` yöntemler, `OpenTextFileReader` **Tüm** sekmesini seçmediğiniz sürece IntelliSense'de görünmeyen gelişmiş yöntemlerdir.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Metin okuyucuiçeren bir dosyadan satır okumak için  
  
- Dosyayı `OpenTextFileReader` belirterek <xref:System.IO.TextReader>açmak için yöntemi kullanın. Bu örnek, adlı `testfile.txt`dosyayı açar, ondan bir satır okur ve satırı bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Okunan dosya bir metin dosyası olmalıdır.  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1.vb dosyası Visual Basic kaynak dosyası olmayabilir.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bir dosyadan okumak için <xref:System.Security.Permissions.FileIOPermission> derlemeniz, sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir. Kısmi güven bağlamında çalışıyorsanız, kod yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir. Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın. Kullanıcının da dosyaya erişmesi gerekir. Daha fazla bilgi için [ACL Technology Genel Bakış'a](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100))bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog Bileşeni](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
