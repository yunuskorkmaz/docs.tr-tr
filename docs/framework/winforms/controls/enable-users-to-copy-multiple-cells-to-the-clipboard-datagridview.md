---
title: Kullanıcıların DataGridView denetiminden panoya birden fazla hücre kopyalamasını sağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: 2bb74a1f0c59b28ab496ce9c89c1c1b5f9d8147b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745775"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma
Hücre kopyalamayı etkinleştirdiğinizde, <xref:System.Windows.Forms.DataGridView> denetimindeki verileri, <xref:System.Windows.Forms.Clipboard>üzerinden diğer uygulamalar için kolayca erişilebilir hale getirebilirsiniz. Seçilen hücrelerin değerleri dizelere dönüştürülür ve Not defteri ve Excel gibi uygulamalara yapıştırılmasına yönelik sekmeyle ayrılmış metin değerleri olarak panoya ve Word gibi uygulamalara yapıştırılmasına yönelik HTML biçimli bir tablo olarak eklenir.  
  
 Hücre kopyalamayı yalnızca hücre değerlerini kopyalamak, pano verilerine satır ve sütun üst bilgi metnini dahil etmek veya yalnızca kullanıcılar tüm satırları veya sütunları seçerken başlık metnini eklemek için yapılandırabilirsiniz.  
  
 Kullanıcılar seçim moduna bağlı olarak, birden fazla bağlantısı kesilmiş hücre grubunu seçebilir. Bir Kullanıcı panoya hücre kopyadığında, seçili hücreleri olmayan satırlar ve sütunlar kopyalanmaz. Diğer tüm satırlar veya sütunlar, panoya kopyalanmış veri tablosunda satır ve sütun haline gelir. Bu satırlardaki veya sütunlardaki seçilmemiş hücreler, panoya boş yer tutucular olarak kopyalanır.  
  
### <a name="to-enable-cell-copying"></a>Hücre kopyalamayı etkinleştirmek için  
  
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> özelliğini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, hücrelerin Pano 'ya nasıl kopyalandığı gösterilmektedir. Bu örnek, <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> yöntemini kullanarak seçili hücreleri panoya kopyalayan ve Pano içeriğini bir metin kutusunda görüntüleyen bir düğme içerir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kod şunları gerektirir:  
  
- N:System ve N:System.Windows.Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
