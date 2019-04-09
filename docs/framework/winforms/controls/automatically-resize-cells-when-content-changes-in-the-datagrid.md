---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 7acd7777ede726b9dfed2b821e4248a0ebf7797f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182500"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma
Yapılandırabileceğiniz <xref:System.Windows.Forms.DataGridView> satırları, sütunları yeniden boyutlandırmak için Denetim ve üst bilgileri otomatik olarak her içerik değişiklikleri, hücre her zaman değerlerine kırpma olmadan görüntülemek için büyük olacak şekilde.  
  
 Hangi hücrelerin yeni boyutlar belirlemek için kullanılan kısıtlamak için birçok seçeneğiniz vardır. Örneğin, yalnızca şu anda görüntülenen satırların değerlere göre sütunların genişliğini otomatik olarak yeniden boyutlandırmak için denetimi yapılandırabilirsiniz. Bu durumda, boyutlandırma yöntemleri gibi kullanmak isteyebilirsiniz ancak bu, Etkisizliği çok sayıda satırı, ile çalışırken önleyebilirsiniz <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> bazen ettiğiniz boyutlarını ayarlamak için.  
  
 Otomatik yeniden boyutlandırma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 Aşağıdaki kod örneği, otomatik olarak yeniden boyutlandırmak için kullanılabilir seçenekleri gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
-   Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
