---
title: 'Nasıl yapılır: StreamReader Olan Dosyalardan Metin Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 6d05dac9b612659a74e25c0ce87c7524316d31a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411609"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Nasıl Yapılır: StreamReader Olan Dosyalardaki Metni Okuma (Visual Basic)

`My.Computer.FileSystem`Nesnesi, <xref:System.IO.TextReader> ve ' i açmak için yöntemler sağlar <xref:System.IO.TextWriter> . Bu yöntemler `OpenTextFileWriter` ve `OpenTextFileReader` , **Tüm** sekmesini seçmediğiniz takdirde IntelliSense 'de görünmeyen gelişmiş yöntemlerdir.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Bir dosyadan metin okuyucu içeren bir satırı okumak için  
  
- `OpenTextFileReader`Öğesini açmak için yöntemini kullanın <xref:System.IO.TextReader> , dosyasını belirtin. Bu örnek, adlı dosyayı açar `testfile.txt` , bundan bir satır okur ve bir ileti kutusunda çizgiyi görüntüler.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Okunan dosya bir metin dosyası olmalıdır.  
  
 Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin. Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.  
  
 Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın. Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bir dosyadan okumak için, derlemeniz sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir <xref:System.Security.Permissions.FileIOPermission> . Kısmi güven bağlamında çalıştırıyorsanız, yetersiz ayrıcalıklar nedeniyle kod bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md). Kullanıcının da dosyaya erişimi olması gerekir. Daha fazla bilgi için bkz. [ACL teknolojisine genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog Bileşeni](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Dosyalardan Okuma](reading-from-files.md)
