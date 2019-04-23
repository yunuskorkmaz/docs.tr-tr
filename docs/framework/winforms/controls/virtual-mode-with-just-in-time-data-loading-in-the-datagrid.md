---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: 6fdf2bd16297820026fa84bdaefe61cc495cea4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169890"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
Aşağıdaki kod örneği, sanal modda kullanmayı gösterilmektedir <xref:System.Windows.Forms.DataGridView> denetimi yalnızca gerekli olduğunda bir sunucudan veri yükleyen bir veri önbelleği ile. Bu örnekte, ayrıntılı olarak açıklanan [ile tam zamanında veri yükleme Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Xml ve System.Windows.Forms derlemelere başvuruları.  
  
-   Yüklü SQL Server Northwind örnek veritabanı ile bir sunucu erişim.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
