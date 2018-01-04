---
title: "Nasıl Yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4898ed7ddff6ca1800ba9380707ad989cbec1125
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Nasıl Yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma
<xref:System.Windows.Forms.DataGridView> Denetimi denetimine veri bağlama aracılığıyla ya da çağırdığınızda ekler tüm satırlar için temel olarak satır şablonunu kullanır <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> kullanmak için var olan bir satır belirtmeden yöntemi.  
  
 Satır şablonunu görünümünü ve davranışını satır üzerinde daha fazla denetim sağlar <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği sağlar. Herhangi bir ayarla Satır şablonuyla <xref:System.Windows.Forms.DataGridViewRow> gibi özelliklerini <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Belirli bir efekt elde etmek için satır şablonunu burada kullanmalısınız bazı durumlar vardır. Örneğin, satır yüksekliği bilgi içinde depolanamaz bir <xref:System.Windows.Forms.DataGridViewCellStyle>, tüm satırları tarafından kullanılan varsayılan yüksekliği değiştirmek için satır şablonunu kullanmanız gerekir. Satır şablonunu de türetilmiş kendi sınıflarınızı oluşturduğunuzda yararlıdır <xref:System.Windows.Forms.DataGridViewRow> ve yeni satırlar için denetim eklendiğinde kullanılan özel türünüz istiyor.  
  
> [!NOTE]
>  Yalnızca satır eklendiğinde satır şablonunu kullanılır. Varolan satırları satır şablonunu değiştirerek değiştiremezsiniz.  
  
### <a name="to-use-the-row-template"></a>Satır şablonunu kullanmak için  
  
-   Kaynağından alınan nesne üzerindeki özellikleri ayarlama <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
