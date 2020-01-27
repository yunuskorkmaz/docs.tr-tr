---
title: DataGridView Denetimindeki bir düğme sütununda düğmeleri devre dışı bırakma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 691781a43005d66e13029ab8110eb7f9daacc35f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745954"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma
<xref:System.Windows.Forms.DataGridView> denetim, bir düğme gibi bir kullanıcı arabirimi (UI) ile hücreleri görüntülemek için <xref:System.Windows.Forms.DataGridViewButtonCell> sınıfını içerir. Ancak <xref:System.Windows.Forms.DataGridViewButtonCell>, hücre tarafından görünen düğmenin görünümünü devre dışı bırakmak için bir yol sağlamaz.  
  
 Aşağıdaki kod örneği, devre dışı görünebilen düğmeleri göstermek için <xref:System.Windows.Forms.DataGridViewButtonCell> sınıfının nasıl özelleştirileceğini gösterir. Örnek, <xref:System.Windows.Forms.DataGridViewButtonCell>türetilen `DataGridViewDisableButtonCell`yeni bir hücre türü tanımlar. Bu hücre türü, hücrede devre dışı bir düğme çizmek için `false` olarak ayarlayabileceğiniz yeni bir `Enabled` özelliği sağlar. Örnek ayrıca, `DataGridViewDisableButtonCell` nesneleri görüntüleyen `DataGridViewDisableButtonColumn`yeni bir sütun türü tanımlar. Bu yeni hücreyi ve sütun türünü göstermek için üst <xref:System.Windows.Forms.DataGridView> her <xref:System.Windows.Forms.DataGridViewCheckBoxCell> geçerli değeri, aynı satırdaki `DataGridViewDisableButtonCell` `Enabled` özelliğinin `true` mi yoksa `false`mi olduğunu belirler.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> türettiğinizde ve türetilmiş sınıfa yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemini geçersiz kıldığınızdan emin olun. Temel sınıfın özelliklerinin yeni hücreye veya sütuna kopyalanabilmesi için temel sınıfın `Clone` yöntemini de çağırmalısınız.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing, System. Windows. Forms ve System. Windows. Forms. VisualStyles derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
