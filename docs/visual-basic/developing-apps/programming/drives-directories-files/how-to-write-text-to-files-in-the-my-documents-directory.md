---
title: "Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 894458ad6d69b8bb2836518b90723703733208b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264525"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma
`My.Computer.FileSystem.SpecialDirectories` Nesnesinin özel dizinleri gibi erişmenizi sağlar **MyDocuments** dizin.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Belgelerim dizini içinde yeni metin dosyaları yazma  
  
1.  Kullanım `My.Computer.FileSystem.SpecialDirectories.MyDocuments` yolunu sağlamak için özellik.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Kullanım `WriteAllText` metni belirtilen dosyaya yazmak için yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Değiştirin `test.txt` yazmak istediğiniz dosyanın adı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu kod, metin dosyasına yazma sırasında oluşabilecek tüm özel durumları yeniden oluşturur. Windows Forms denetimlerini kullanarak özel durumları olasılığını azaltabilirsiniz [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) geçerli dosya adları için kullanıcı seçenekler sınırlandıran bileşenleri. Bu denetimleri kullanarak ancak kusursuz, değildir. Dosya sistemi, bir dosya kullanıcının seçtiği zaman ve kodu yürüten saat arasında değiştirebilirsiniz. Özel durum işleme Bu nedenle neredeyse her zaman dosyalarıyla çalışma ile gereklidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kısmi güven bağlamda çalıştırıyorsanız, kod bir özel durum yetersiz ayrıcalıklar nedeniyle fırlatabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
 Bu örnek, yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulama için klasör oluşturma izniniz gerekiyor. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca yazma izni, daha az ayrıcalıkla gerekir. Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca tek bir dosyayı okuma ayrıcalıkları vermek yerine bir klasör oluşturma ayrıcalıkları vermek için daha güvenli olması. Ayrıca, verileri kullanıcı klasörleri kök klasörüne yazmak için daha güvenli olması veya **Program dosyaları** klasör. Daha fazla bilgi için [ACL teknolojisine genel bakış](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
