---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme"
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
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d57eee9181298ce3afa61a1e7a13d8f092ad68f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme
Görünümünü denetleyebilirsiniz <xref:System.Windows.Forms.DataGridView> satırlara birini veya her ikisini işleme göre <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olaylar. Bu olaylar, yalnızca veren while istediğinizi boyamak şekilde tasarlanmıştır <xref:System.Windows.Forms.DataGridView> denetim boyama rest. Örneğin, özel bir arka plan boyama istiyorsanız, işleyebilir <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olay ve tek tek hücrelere boyamak kendi let ön plan içeriği. Alternatif olarak, kendilerini boyama ve özel ön plan içerik için bir işleyici ekleyin hücreleri sağlayabilirsiniz <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olay. Ayrıca hücre boyama devre dışı bırakın ve içinde her şeyi kendiniz boyamak bir <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olay işleyicisi.  
  
 Aşağıdaki kod örneğinde bir gradyan seçimi arka plan ve birden çok sütuna yayılan bazı özel ön plan içerik sağlamak için her iki olayları için işleyiciler uygular.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Windows Forms DataGridView denetimini özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView denetimi mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
