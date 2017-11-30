---
title: "Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme"
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
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 910730f67024fbe0d292b4a329a36fb3ea8254b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme
Bazen bir iş nesnesi bir koleksiyonda depolanan bilgileri tablosunu görüntülemek yararlıdır. Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> bu tür bir koleksiyon, her bir genel özelliğinin denetimine özelliği ile gözatılamaz dışı olarak işaretlenmiş sürece kendi sütununda görüntülenen bir <xref:System.ComponentModel.BrowsableAttribute>. Örneğin, bir koleksiyonu `Customer` nesneleri sahip olabilir sütunlar gibi **adı** ve **adresi**.  
  
 Bu nesneler ek bilgi ve erişmek istediğiniz kodu içeriyorsa, satır nesnelerde ulaşabilirsiniz. Aşağıdaki kod örneğinde kullanıcıların birden çok satır seçin ve her karşılık gelen müşteriler için bir fatura göndermek için bir düğmeye tıklayın.  
  
### <a name="to-access-row-bound-objects"></a>Satır bağlı nesnelere erişmek için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Örnek  
 Tam kod örneği basit bir içeren `Customer` uygulama ve bağlamalar <xref:System.Windows.Forms.DataGridView> için bir <xref:System.Collections.ArrayList> birkaç içeren `Customer` nesneleri. <xref:System.Windows.Forms.Control.Click> Olay işleyicisi <xref:System.Windows.Forms.Button?displayProperty=nameWithType> erişmesi gereken `Customer` müşteri koleksiyonu dışında erişilebilir olmadığı için satır nesneleri <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView denetiminde verileri görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetimlerine nesne bağlama](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)
