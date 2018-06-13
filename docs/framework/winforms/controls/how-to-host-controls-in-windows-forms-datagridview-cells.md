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
ms.openlocfilehash: 730a0677dbc405617c7075402ba0c20dfbd8724d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534053"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma
<xref:System.Windows.Forms.DataGridView> Denetimi girin ve çeşitli şekillerde değerlerini düzenlemek, kullanıcılarınızın etkinleştirme birkaç sütun türleri sağlar. Ancak, bu sütun türleri veri girişi gereksinimlerinizi karşılamazsa, seçtiğiniz denetimleri konak hücrelerle kendi sütun türleri oluşturabilirsiniz. Bunu yapmak için öğesinden türetilen sınıflarını tanımlamak <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.DataGridViewCell>. Türetilen bir sınıfı tanımlamanız gerekir <xref:System.Windows.Forms.Control> ve uygulayan <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.  
  
 Aşağıdaki kod örneğinde bir takvim sütun oluşturulacağını gösterir. Bu sütunun hücre normal metin kutusu hücrelerindeki, ancak kullanıcı hücrenin düzenlediğinde tarihleri görüntüleme bir <xref:System.Windows.Forms.DateTimePicker> denetimi görünür. Metin kutusu görüntü işlevlerini yeniden uygulamak zorunda kalmamak için `CalendarCell` sınıfı türer <xref:System.Windows.Forms.DataGridViewTextBoxCell> devralma yerine sınıfı <xref:System.Windows.Forms.DataGridViewCell> doğrudan sınıfı.  
  
> [!NOTE]
>  Türetilen zaman <xref:System.Windows.Forms.DataGridViewCell> veya <xref:System.Windows.Forms.DataGridViewColumn> ve türetilen sınıfın yeni özellikler ekleme, geçersiz kılmak mutlaka `Clone` kopyalama işlemleri sırasında yeni özellikleri kopyalamak için yöntem. Temel sınıfın da çağırmalıdır `Clone` yöntemi böylece temel sınıfının özelliklerini yeni hücresinde veya sütununda kopyalanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView Denetimi Mimarisi](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows Forms DataGridView Denetiminde Sütun Türleri](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
