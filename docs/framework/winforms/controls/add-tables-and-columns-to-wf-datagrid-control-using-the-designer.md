---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimine Tablolar ve Sütunlar Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: d11c4f7e4cdfb597477bb99f38612ed648849f20
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040048"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimine Tablolar ve Sütunlar Ekleme

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

<xref:System.Windows.Forms.DataGrid> Nesneler oluşturarak <xref:System.Windows.Forms.DataGridTableStyle> <xref:System.Windows.Forms.DataGrid>vebunları denetimin özelliğindenerişilennesnesineekleyerektablovesütunlardakiWindowsFormsdenetimindekiverilerigörüntüleyebilirsiniz.<xref:System.Windows.Forms.DataGrid.TableStyles%2A> <xref:System.Windows.Forms.GridTableStylesCollection> Her tablo stili, <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGridTableStyle>öğesinin özelliğinde belirtilen veri tablosunun içeriğini görüntüler. Varsayılan olarak, sütun stilleri olmayan bir tablo stili, bu veri tablosu içindeki tüm sütunları görüntüler. <xref:System.Windows.Forms.DataGridColumnStyle> <xref:System.Windows.Forms.GridColumnStylesCollection>Her birininözelliği<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> aracılığıyla erişilen öğesine nesneler ekleyerek tablodaki sütunları sınırlayabilirsiniz. <xref:System.Windows.Forms.DataGridTableStyle>

Aşağıdaki yordamlar, bir <xref:System.Windows.Forms.DataGrid> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Bu tür bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin. Visual Studio 2005 ' <xref:System.Windows.Forms.DataGrid> de varsayılan olarak denetim **araç kutusunda**değildir. Ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Araç kutusuna](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))öğe ekleyin.

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Tasarımcıda DataGrid denetimine tablo eklemek için

1. Tablodaki verileri göstermek için öncelikle <xref:System.Windows.Forms.DataGrid> denetimi bir veri kümesine bağlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Tasarımcı](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)kullanarak Windows Forms DataGrid denetimini bir veri kaynağına bağlayın.

2. <xref:System.Windows.Forms.DataGrid> Özellikler penceresi![](./media/visual-studio-ellipsis-button.png)denetimin özelliğini seçin ve ardından, özelliğin yanındaki üç nokta düğmesini (Visual Studio Özellikler penceresi (...) tıklayın. <xref:System.Windows.Forms.DataGrid.TableStyles%2A> **DataGridTableStyle koleksiyon Düzenleyicisi**.

3. Koleksiyon Düzenleyicisi 'nde tablo stili eklemek için **Ekle** ' ye tıklayın.

4. Koleksiyon düzenleyicisini kapatmak için **Tamam** ' ı tıklatın ve ardından <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliğin yanındaki üç nokta düğmesine tıklayarak yeniden açın.

     Koleksiyon düzenleyicisini yeniden açtığınızda, denetime bağlanacak tüm veri tabloları tablo stilinin <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği için açılan listede görüntülenir.

5. Koleksiyon düzenleyicisinin **Üyeler** kutusunda tablo stiline tıklayın.

6. Koleksiyon Düzenleyicisi 'nin **Özellikler** kutusunda, göstermek istediğiniz tablo için <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> değeri seçin.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Tasarımcıda DataGrid denetimine bir sütun eklemek için

1. **DataGridTableStyle koleksiyonu düzenleyicisinin** **Üyeler** kutusunda uygun tablo stilini seçin. Koleksiyon Düzenleyicisi 'nin **Özellikler** kutusunda, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonu seçin ve sonra, özelliğin yanındaki üç nokta düğmesini![(Visual Studio Özellikler penceresi) tıklatın.](./media/visual-studio-ellipsis-button.png) **DataGridColumnStyle koleksiyon düzenleyicisini**görüntüleyin.

2. Koleksiyon Düzenleyicisi 'nde, sütun stili eklemek için **Ekle** ' ye tıklayın veya bir sütun türü belirtmek için **Ekle** ' nin yanındaki aşağı oka tıklayın.

     Açılan kutuda <xref:System.Windows.Forms.DataGridTextBoxColumn> ya <xref:System.Windows.Forms.DataGridBoolColumn> da türünü seçebilirsiniz.

3. Tamam ' a tıklayarak **DataGridColumnStyle koleksiyon düzenleyicisini**kapatın ve sonra <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliğin yanındaki üç nokta düğmesine tıklayarak yeniden açın.

     Koleksiyon düzenleyicisini yeniden açtığınızda, ilişkili veri tablosundaki tüm veri sütunları, sütun stilinin <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> özelliği için açılan listede görüntülenir.

4. Koleksiyon düzenleyicisinin **Üyeler** kutusunda sütun stiline tıklayın.

5. Koleksiyon Düzenleyicisi 'nin **Özellikler** kutusunda, göstermek istediğiniz sütunun <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> değerini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
