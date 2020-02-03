---
title: DataGridView denetiminde tam zamanında veri yükleme ile sanal modu uygulama
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
ms.openlocfilehash: bbe98d3c317a7625b36b729f0be23ea20f65dec0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745430"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama
Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView> denetimindeki sanal modun, verileri yalnızca gerektiğinde bir sunucudan yükleyen bir veri önbelleği ile nasıl kullanılacağını gösterir. Bu örnek, [Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)konusunda ayrıntılı olarak açıklanmıştır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. xml ve System. Windows. Forms derlemelerine başvurular.  
  
- Northwind SQL Server örnek veritabanının yüklü olduğu bir sunucuya erişim.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
