---
title: "Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a756be7f61c812269d5ee08d99ccf6785ddcc7df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma
`My.Computer.FileSystem.SpecialDirectories` Nesne özel dizinleri gibi erişmenizi sağlar **MyDocuments** dizin.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Belgelerim dizini yeni metin dosyaları yazma  
  
1.  Kullanım `My.Computer.FileSystem.SpecialDirectories.MyDocuments` özelliği yolunu sağlayın.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Kullanım `WriteAllText` metni belirtilen dosyaya yazmak için yöntem.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Değiştir `test.txt` yazmak istediğiniz dosyanın adı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu kod metin dosyasına yazma sırasında meydana gelebilecek tüm özel durumları yeniden oluşturur. Windows Forms denetimleri gibi kullanarak özel durumlar olasılığını azaltabilir [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) geçerli dosya adları için kullanıcı seçimlerini sınırlamak bileşenleri. Bu denetimleri kullanarak ancak kusursuz, değildir. Dosya sistemi, kullanıcı bir dosyayı seçtiğinde ve kodu yürütür saat arasında değiştirebilirsiniz. Özel durum işleme Bu nedenle neredeyse her zaman dosyalarıyla çalışma zaman ile gereklidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kısmi güven bağlamda çalıştırıyorsanız, kodu nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
 Bu örnekte yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmak gerekirse, bu uygulama için klasör oluşturma izniniz gerekiyor. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca yazma izni, daha düşük ayrıcalık gerekir. Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca tek bir dosya için okuma ayrıcalıkları vermek yerine bir klasör oluşturma ayrıcalığı vermek için daha güvenli olan. Ayrıca, verileri kullanıcı klasörleri kök klasörüne yazmak için daha güvenli olan veya **Program Files** klasör. Daha fazla bilgi için bkz: [ACL teknoloji genel bakış](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
