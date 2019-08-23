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
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967390"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma
Denetim, bir düğme <xref:System.Windows.Forms.DataGridViewButtonCell> gibi bir kullanıcı arabirimi (UI) ile hücreleri görüntülemek için sınıfını içerir. <xref:System.Windows.Forms.DataGridView> Ancak, <xref:System.Windows.Forms.DataGridViewButtonCell> hücre tarafından görünen düğmenin görünümünü devre dışı bırakmak için bir yol sağlamaz.  
  
 Aşağıdaki kod örneği, devre dışı görünebilen düğmeleri <xref:System.Windows.Forms.DataGridViewButtonCell> göstermek için sınıfının nasıl özelleştirileceğini gösterir. Örnek, `DataGridViewDisableButtonCell`' den <xref:System.Windows.Forms.DataGridViewButtonCell>türetilen yeni bir hücre türü tanımlar. Bu hücre türü, hücrede devre `Enabled` dışı bir düğme çizmek için olarak `false` ayarlanabilir yeni bir özellik sağlar. Örnek ayrıca, nesneleri görüntüleyen `DataGridViewDisableButtonColumn` `DataGridViewDisableButtonCell` yeni bir sütun türü tanımlar. Bu yeni hücreyi ve sütun türünü göstermek için, <xref:System.Windows.Forms.DataGridViewCheckBoxCell> üst öğede <xref:System.Windows.Forms.DataGridView> her birinin geçerli değeri, aynı satırdaki `Enabled` öğesinin `DataGridViewDisableButtonCell` özelliğinin veya `false`olduğunu `true` belirler.  
  
> [!NOTE]
> Türetilmiş sınıfa türeten <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> yeni özellikler eklediğinizde, kopyalama işlemleri sırasında yeni özellikleri kopyalamak için `Clone` yöntemi geçersiz kıldığınızdan emin olun. Ayrıca temel sınıfın özelliklerini yeni hücreye veya sütuna `Clone` kopyalamak için temel sınıfın yöntemini çağırmanız gerekir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing, System. Windows. Forms ve System. Windows. Forms. VisualStyles derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
