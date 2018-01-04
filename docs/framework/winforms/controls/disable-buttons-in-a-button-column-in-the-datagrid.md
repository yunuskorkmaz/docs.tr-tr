---
title: "Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma"
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
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb16014003540219c789b05e4ccd7f023a98b5c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma
<xref:System.Windows.Forms.DataGridView> Denetimi içeren <xref:System.Windows.Forms.DataGridViewButtonCell> düğmesi gibi bir kullanıcı arabirimi (UI) hücrelerle görüntüleme sınıfı. Ancak, <xref:System.Windows.Forms.DataGridViewButtonCell> hücre tarafından görüntülenen düğmeye görünümünü devre dışı bırakmak için bir yol sağlamaz.  
  
 Aşağıdaki kod örneğinde nasıl özelleştirileceğini gösteren <xref:System.Windows.Forms.DataGridViewButtonCell> devre dışı görünebilir düğmeleri görüntülemek için sınıf. Örneğin yeni bir hücre türünü tanımlayan `DataGridViewDisableButtonCell`, türetilen <xref:System.Windows.Forms.DataGridViewButtonCell>. Bu hücreyi türü yeni bir sağlar `Enabled` ayarlanabilir özelliği `false` devre dışı bırakılmış bir düğme hücrede çizmek için. Örnek ayrıca yeni bir sütun türü tanımlar `DataGridViewDisableButtonColumn`, görüntüleyen `DataGridViewDisableButtonCell` nesneleri. Göstermek için bu yeni hücreye ve sütun türü, her geçerli değeri <xref:System.Windows.Forms.DataGridViewCheckBoxCell> üst <xref:System.Windows.Forms.DataGridView> belirler olup olmadığını `Enabled` özelliği `DataGridViewDisableButtonCell` aynı sırada `true` veya `false`.  
  
> [!NOTE]
>  Türetilen zaman <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilen sınıfın yeni özellikler ekleme, geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntem. Temel sınıfın da çağırmalıdır `Clone` yöntemi böylece temel sınıfının özelliklerini yeni hücresinde veya sütununda kopyalanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing, System.Windows.Forms ve System.Windows.Forms.VisualStyles derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView Denetimi Mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
