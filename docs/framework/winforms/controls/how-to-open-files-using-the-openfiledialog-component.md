---
title: 'Nasıl yapılır: OpenFileDialog bileşeniyle dosya açma'
ms.date: 02/11/2019
description: Dosya tarama ve seçme için Windows iletişim kutusunu açmak üzere OpenFileDialog bileşenini nasıl kullanacağınızı öğrenin.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904435"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Nasıl yapılır: OpenFileDialog ile dosyaları açma

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>Bileşen, dosyalara gözatmak ve seçmek Için Windows iletişim kutusunu açar. Seçili dosyaları açmak ve okumak için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> yöntemini kullanabilir veya sınıfının bir örneğini oluşturabilirsiniz <xref:System.IO.StreamReader?displayProperty=nameWithType> . Aşağıdaki örneklerde her iki yaklaşım gösterilmektedir.

.NET Framework, özelliği almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> sınıfı tarafından verilen ayrıcalık düzeyi gereklidir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> . Örnekler bir <xref:System.Security.Permissions.FileIOPermission> izin denetimi çalıştırır ve kısmi güven bağlamında çalıştırıldıysanız ayrıcalıkların yetersiz olması nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamalar olarak oluşturabilir ve çalıştırabilirsiniz. Daha fazla bilgi için, komut satırından csc.exeveya [derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) [ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) bölümüne bakın.

.NET Core 3,0 ile başlayarak, örnekleri .NET Core Windows Forms * \<folder name> . csproj* proje dosyası olan bir klasörden Windows .NET Core uygulamaları olarak oluşturup çalıştırabilirsiniz.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Örnek: StreamReader ile bir dosyayı akış olarak okuma  
  
Aşağıdaki örnek, <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> yöntemi ile açmak için Windows Forms denetimin olay işleyicisini kullanır <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> . Kullanıcı bir dosya seçtikten ve **Tamam**seçeneğini belirledikten sonra, sınıfın bir örneği <xref:System.IO.StreamReader> dosyayı okur ve formun metin kutusunda içeriğini görüntüler. Dosya akışlarından okuma hakkında daha fazla bilgi için bkz <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> . ve <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Örnek: bir filtrelenmiş seçimden bir dosyayı OpenFile ile açma

Aşağıdaki örnek <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> , <xref:System.Windows.Forms.OpenFileDialog> yalnızca metin dosyalarını gösteren bir filtre ile açmak için denetimin olay işleyicisini kullanır. Kullanıcı bir metin dosyası seçtikten ve **Tamam**' ı seçerse, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dosyayı Not defteri 'nde açmak için yöntemi kullanılır.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog bileşeni](openfiledialog-component-windows-forms.md)
