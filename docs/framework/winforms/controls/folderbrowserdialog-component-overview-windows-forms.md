---
title: FolderBrowserDialog bileşenine genel bakış
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745731"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, klasörlere göz atmak ve klasörler seçmek için kullanılan bir kalıcı iletişim kutusudur. Yeni klasörler, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni içinden de oluşturulabilir.

> [!NOTE]
> Klasörler yerine dosyaları seçmek için [OpenFileDialog](openfiledialog-component-windows-forms.md) bileşenini kullanın.

<xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi kullanılarak çalışma zamanında görüntülenir. En üstteki klasörü ve iletişim kutusunun ağaç görünümünde görünecek alt klasörleri öğrenmek için <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> özelliğini ayarlayın. İletişim kutusu gösterildikten sonra, seçilen klasörün yolunu almak için <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliğini kullanabilirsiniz.

Bir forma eklendiğinde <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog Bileşeni](folderbrowserdialog-component-windows-forms.md)
