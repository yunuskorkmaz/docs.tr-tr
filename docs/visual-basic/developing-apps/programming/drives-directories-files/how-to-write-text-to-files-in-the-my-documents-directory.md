---
title: 'Nasıl Yapılır: Belgelerim Dizinindeki Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334519"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma

Nesne, `My.Computer.FileSystem.SpecialDirectories` **MyDocuments** dizini gibi özel dizinlere erişmenizi sağlar.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Belgelerim dizinine yeni metin dosyaları yazmak için  
  
1. Yolu `My.Computer.FileSystem.SpecialDirectories.MyDocuments` sağlamak için özelliği kullanın.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Belirtilen `WriteAllText` dosyaya metin yazmak için yöntemi kullanın.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Yazmak `test.txt` istediğiniz dosyanın adı ile değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu kod, dosyaya metin yazarken oluşabilecek tüm özel durumları yeniden atar. Kullanıcı seçeneklerini geçerli dosya adlarıyla sınırlayan [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) ve [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) bileşenleri gibi Windows Forms denetimlerini kullanarak özel durumlar olasılığını azaltabilirsiniz. Ancak, bu denetimleri kullanarak kusursuz değildir. Dosya sistemi, kullanıcının bir dosyayı seçtiği saat ile kodun yürütüldettiği saat arasında değişebilir. Bu nedenle, dosyalarla çalışırken özel durum işleme neredeyse her zaman gereklidir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Kısmi güven bağlamında çalışıyorsanız, kod yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir. Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.  
  
 Bu örnek yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için oluşturma iznine ihtiyacı vardır. İzinler erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca yazma iznine, daha az bir ayrıcalığa ihtiyacı vardır. Mümkün olduğunda, dosyayı dağıtım sırasında oluşturmak ve bir klasör için ayrıcalık oluştur'a ayrıcalık vermek yerine yalnızca tek bir dosyaya Okuma ayrıcalıkları vermek daha güvenlidir. Ayrıca, kullanıcı klasörlerine veri yazmak kök klasöre veya **Program Dosyaları** klasörüne yazmaktan daha güvenlidir. Daha fazla bilgi için [ACL Technology Genel Bakış'a](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100))bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
