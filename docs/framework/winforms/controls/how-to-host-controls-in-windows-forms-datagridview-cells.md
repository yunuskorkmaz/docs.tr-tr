---
title: 'Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 008b6da56c3428d0edcc44778b4d3bef1a52c443
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194207"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma
<xref:System.Windows.Forms.DataGridView> Denetim kullanıcılarınızın girin ve çeşitli şekillerde değerlerini düzenlemek birden fazla sütun türleri sağlar. Ancak, bu sütun türleri veri girişi gereksinimlerinizi karşılamıyorsa, seçtiğiniz denetimleri barındıran hücrelerin ile kendi sütun türleri oluşturabilirsiniz. Bunu yapmak için türetilen sınıfları tanımlama <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>. Türetilen bir sınıf da tanımlamanız gerekir <xref:System.Windows.Forms.Control> ve uygulayan <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.  
  
 Aşağıdaki kod örneği, bir takvim sütun oluşturmak gösterilmektedir. Bu sütunun hücre normal metin kutusu hücrelerindeki, ancak kullanıcı bir hücreye düzenlediğinde tarihleri görüntüleme bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür. Metin kutusunun görüntüleme işlevlerini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıf türetilir <xref:System.Windows.Forms.DataGridViewTextBoxCell> sınıf devralma yerine <xref:System.Windows.Forms.DataGridViewCell> doğrudan sınıf.  
  
> [!NOTE]
>  Olduğunda, türetilen <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilmiş sınıf için yeni özellikler eklemek için geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntemi. Ayrıca temel sınıfın çağırmalıdır `Clone` yöntemi, böylece yeni hücresinde veya sütununda için temel sınıf özelliklerini kopyalanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
- [Windows Forms DataGridView Denetiminde Sütun Türleri](column-types-in-the-windows-forms-datagridview-control.md)
