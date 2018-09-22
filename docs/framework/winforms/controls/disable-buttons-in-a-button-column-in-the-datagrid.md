---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 0687b4e4c3896e7663c5c093a43a2db72e0053f8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697587"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma
<xref:System.Windows.Forms.DataGridView> Denetimi içeren <xref:System.Windows.Forms.DataGridViewButtonCell> hücre bir düğme gibi bir kullanıcı arabirimi (UI) görüntülemek için sınıf. Ancak, <xref:System.Windows.Forms.DataGridViewButtonCell> hücrenin tarafından görüntülenen düğmesinin devre dışı bırakmak için bir yöntem sağlamaz.  
  
 Aşağıdaki kod örneğinde nasıl özelleştirileceğini gösterir <xref:System.Windows.Forms.DataGridViewButtonCell> devre dışı görünebilen düğmeleri görüntülemek için sınıf. Örnek yeni bir hücre türü tanımlar `DataGridViewDisableButtonCell`, türetilen <xref:System.Windows.Forms.DataGridViewButtonCell>. Bu hücre türü yeni bir sağlar `Enabled` ayarlanabilir özelliği `false` hücrede devre dışı bırakılmış bir düğme çizmek için. Örnek ayrıca yeni bir sütun türü tanımlar `DataGridViewDisableButtonColumn`, görüntüleyen `DataGridViewDisableButtonCell` nesneleri. Göstermek için bu yeni hücreyi ve sütun türü, her geçerli değerini <xref:System.Windows.Forms.DataGridViewCheckBoxCell> üst <xref:System.Windows.Forms.DataGridView> belirler olmadığını `Enabled` özelliği `DataGridViewDisableButtonCell` aynı sırada `true` veya `false`.  
  
> [!NOTE]
>  Olduğunda, türetilen <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıf için yeni özellikler eklemek için geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi. Ayrıca temel sınıfın çağırmalıdır `Clone` yöntemi, böylece yeni hücresinde veya sütununda için temel sınıf özelliklerini kopyalanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing, System.Windows.Forms ve System.Windows.Forms.VisualStyles derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView Denetimi Mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
