---
title: 'Nasıl açılır: OpenFileDialog bileşeni ile dosyaları açın'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182126"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Nasıl yapılı: OpenFileDialog ile dosyaları açın

Bileşen, <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> dosyaları tarama ve seçmek için Windows iletişim kutusunu açar. Seçili dosyaları açıp okumak için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> yöntemi kullanabilir veya sınıfın bir <xref:System.IO.StreamReader?displayProperty=nameWithType> örneğini oluşturabilirsiniz. Aşağıdaki örnekler her iki yaklaşımı da göstermektedir.

.NET Framework'de, <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği almak veya ayarlamak için <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir. Örnekler bir <xref:System.Security.Permissions.FileIOPermission> izin denetimi çalıştırın ve kısmi güven bağlamında çalıştırılırsa yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir. Daha fazla bilgi için [Kod erişim güvenlik temellerine](../../misc/code-access-security-basics.md)bakın.

Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamaları olarak oluşturabilir ve çalıştırabilirsiniz. Daha fazla bilgi için [csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [Build komut satırına](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)sahip Command-line binasına bakın.

.NET Core 3.0 ile başlayarak, .NET Core Windows Forms * \<klasör adı>.csproj* proje dosyasına sahip bir klasörden windows .NET Core uygulamaları olarak örnekler oluşturabilir ve çalıştırabilirsiniz.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Örnek: Bir dosyayı StreamReader ile akış olarak okuyun  
  
<xref:System.Windows.Forms.Button> Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.OpenFileDialog> yöntemle açmak için Windows Forms denetiminin olay işleyicisi <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> kullanır. Kullanıcı bir dosya yı seçip **Tamam'ı**seçtikten sonra sınıfın bir örneği dosyayı <xref:System.IO.StreamReader> okur ve içeriğini formun metin kutusunda görüntüler. Dosya akışlarından okuma hakkında daha <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> fazla <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>bilgi için bkz.  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Örnek: OpenFile ile filtre uygulanmış bir seçimden dosya açma

Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> yalnızca <xref:System.Windows.Forms.Control.Click> metin dosyalarını gösteren <xref:System.Windows.Forms.OpenFileDialog> bir filtreyi açmak için denetimin olay işleyicisi kullanır. Kullanıcı bir metin dosyası seçtikten ve **Tamam'ı**seçtikten sonra, dosyayı <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Not Defteri'nde açmak için yöntem kullanılır.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog bileşeni](openfiledialog-component-windows-forms.md)
