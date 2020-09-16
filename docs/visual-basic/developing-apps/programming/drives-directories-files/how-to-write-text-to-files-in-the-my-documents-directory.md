---
title: 'Nasıl yapılır: Belgelerim Dizinindeki Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bb3a9bdc44f86fbcdb3c56ee088740efdfebe95d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546464"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma

`My.Computer.FileSystem.SpecialDirectories`Nesnesi, **MyDocuments** dizini gibi özel dizinlere erişmenizi sağlar.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Yeni metin dosyalarını Belgelerim dizinine yazmak için  
  
1. `My.Computer.FileSystem.SpecialDirectories.MyDocuments`Yolunu sağlamak için özelliğini kullanın.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. `WriteAllText`Belirtilen dosyaya metin yazmak için yöntemini kullanın.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 `test.txt`Yazmak istediğiniz dosyanın adıyla değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bu kod, dosyaya metin yazarken ortaya çıkabilecek tüm özel durumları yeniden oluşturur. Kullanıcı seçimlerini geçerli dosya adlarıyla sınırlayan [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) ve [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) bileşenleri gibi Windows Forms denetimleri kullanarak özel durumların olasılığını azaltabilirsiniz. Ancak, bu denetimlerin kullanılması, örnek değildir. Dosya sistemi, kullanıcının bir dosyayı seçtiği zaman ve kodun yürütüldüğü saat arasında değişebilir. Bu nedenle, dosyalarla çalışırken neredeyse her zaman özel durum işleme gerekir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Kısmi güven bağlamında çalıştırıyorsanız, yetersiz ayrıcalıklar nedeniyle kod bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
 Bu örnek yeni bir dosya oluşturur. Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için oluşturma izni olması gerekir. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten mevcutsa, uygulamanın daha az bir ayrıcalık olmak üzere yalnızca yazma izni olması gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve bir klasör için oluşturma ayrıcalıkları vermek yerine yalnızca tek bir dosyaya okuma ayrıcalıkları verin. Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya **Program Files** klasöründen daha güvenlidir. Daha fazla bilgi için bkz. [ACL teknolojisine genel bakış](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
