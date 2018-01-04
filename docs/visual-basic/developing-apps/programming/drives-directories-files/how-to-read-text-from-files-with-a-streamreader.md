---
title: "Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b306c0e32f619a3e351cd08524767a44cee8005
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)
`My.Computer.FileSystem` Nesne açmak için yöntemler sağlar bir <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter>. Bu yöntemler `OpenTextFileWriter` ve `OpenTextFileReader`, seçtiğiniz sürece IntelliSense içinde görünmez yöntemleri Gelişmiş **tüm** sekmesi.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Bir satır bir metin okuyucu bir dosyasından okunamıyor  
  
-   Kullanım `OpenTextFileReader` açmak için yöntemini <xref:System.IO.TextReader>, dosya belirtme. Bu örnek adlı dosyayı açar `testfile.txt`, bir satır ondan okur ve satırı bir ileti kutusu görüntüler.  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Salt okunur dosya bir metin dosyası olmalıdır.  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, dosya Form1.vb bir Visual Basic kaynak dosyası olmayabilir.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir dosyadan okunan için derlemenizi ayrıcalık düzeyi verilen tarafından gerektirir <xref:System.Security.Permissions.FileIOPermission> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, kodu nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md). Kullanıcının dosyaya erişim de gerekir. Daha fazla bilgi için bkz: [ACL teknoloji genel bakış](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>  
 [SaveFileDialog Bileşeni](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)  
 [Dosyalardan Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
