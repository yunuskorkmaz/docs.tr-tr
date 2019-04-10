---
title: "Nasıl yapılır: Dosyalara metin yazma Visual Basic'te Belgelerim dizini"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 4f9eb4c9e0eb92712b5ea1a4feef24f2bb95d70b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335465"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Nasıl yapılır: Dosyalara metin yazma Visual Basic'te Belgelerim dizini
`My.Computer.FileSystem.SpecialDirectories` Nesnesinin özel dizinleri gibi erişmenizi sağlar **MyDocuments** dizin.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Belgelerim dizini içinde yeni metin dosyaları yazma  
  
1. Kullanım `My.Computer.FileSystem.SpecialDirectories.MyDocuments` yolunu sağlamak için özellik.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Kullanım `WriteAllText` metni belirtilen dosyaya yazmak için yöntemi.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Değiştirin `test.txt` yazmak istediğiniz dosyanın adı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu kod, metin dosyasına yazma sırasında oluşabilecek tüm özel durumları yeniden oluşturur. Windows Forms denetimlerini kullanarak özel durumları olasılığını azaltabilirsiniz [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) geçerli dosya adları için kullanıcı seçenekler sınırlandıran bileşenleri. Bu denetimleri kullanarak ancak kusursuz, değildir. Dosya sistemi, bir dosya kullanıcının seçtiği zaman ve kodu yürüten saat arasında değiştirebilirsiniz. Özel durum işleme Bu nedenle neredeyse her zaman dosyalarıyla çalışma ile gereklidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kısmi güven bağlamda çalıştırıyorsanız, kod bir özel durum yetersiz ayrıcalıklar nedeniyle fırlatabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
 Bu örnek, yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulama için klasör oluşturma izniniz gerekiyor. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca yazma izni, daha az ayrıcalıkla gerekir. Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca tek bir dosyayı okuma ayrıcalıkları vermek yerine bir klasör oluşturma ayrıcalıkları vermek için daha güvenli olması. Ayrıca, verileri kullanıcı klasörleri kök klasörüne yazmak için daha güvenli olması veya **Program dosyaları** klasör. Daha fazla bilgi için [ACL teknolojisine genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
