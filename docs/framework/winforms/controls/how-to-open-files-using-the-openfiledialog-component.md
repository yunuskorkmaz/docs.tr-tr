---
title: 'Nasıl yapılır: OpenFileDialog bileşeni ile açık dosyalar'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 5781543a61d77ef8f0658e95759c57fdb77cfc4f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723094"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Nasıl yapılır: OpenFileDialog ile açık dosyalar 

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> Bileşeni göz atma ve dosyalar seçmek için Windows iletişim kutusunu açar. Seçili dosyaları açmak ve okumak için kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> yöntemi veya bir örneğini oluşturmak <xref:System.IO.StreamReader?displayProperty=nameWithType> sınıfı. Aşağıdaki örnekler, iki yaklaşımı gösterir. 

.NET Framework'teki almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği gerektiren bir ayrıcalık düzeyi verilmiş tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Örnekleri çalıştırmak bir <xref:System.Security.Permissions.FileIOPermission> izni denetleyin ve bir özel durum yetersiz ayrıcalıklar nedeniyle bir kısmi güven bağlamında çalıştırırsanız atabilirsiniz. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).

Derleme ve bu örnekler, .NET Framework uygulamaları Çalıştır C# veya Visual Basic komut satırı. Daha fazla bilgi için [csc.exe ile komut satırı derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

.NET Core 3.0 ile başlayarak, ayrıca yapı ve örnekler Windows .NET Core uygulamaları .NET Core Windows Forms bir klasörden Çalıştır  *\<klasör adı > .csproj* proje dosyası. 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Örnek: StreamReader olan bir akış olarak bir dosyayı okuma  
  
Aşağıdaki örnek Windows Forms kullanan <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> açmak için olay işleyicisi <xref:System.Windows.Forms.OpenFileDialog> ile <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi. Kullanıcı bir dosya seçer ve seçer sonra **Tamam**, örneği <xref:System.IO.StreamReader> sınıf dosyasını okur ve form denetiminin metin kutusuna içeriğini görüntüler. Dosya akışları okuma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Örnek: Openfıle ile filtre uygulanmış bir seçimin bir dosyayı açma 

Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> açmak için olay işleyicisi <xref:System.Windows.Forms.OpenFileDialog> bir filtreyle yalnızca metin dosyaları gösterir. Kullanıcı bir metin dosyası seçer ve seçer sonra **Tamam**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyasını Not Defteri'nde açmak için kullanılır.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog bileşeni](openfiledialog-component-windows-forms.md)
