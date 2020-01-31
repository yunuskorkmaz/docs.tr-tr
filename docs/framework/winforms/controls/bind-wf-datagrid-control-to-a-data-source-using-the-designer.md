---
title: Tasarımcı kullanarak DataGrid denetimini bir veri kaynağına bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744092"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimini Veri Kaynağına Bağlama

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır. <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırarak çalışma zamanında denetimi tasarım zamanında bağlarsınız. Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.

 Veri kaynağı tasarım zamanında kullanılabiliyorsa — Örneğin, form bir veri kümesinin veya bir veri görünümünün örneğini içeriyorsa — tasarım zamanında Kılavuzu veri kaynağına bağlayabilirsiniz. Ardından, verilerin kılavuzda nasıl görüneceğine ilişkin önizleme yapabilirsiniz.

 Ayrıca, çalışma zamanında Kılavuzu programlı bir şekilde bağlayabilirsiniz. Bu, çalışma zamanında aldığınız bilgilere göre bir veri kaynağı ayarlamak istediğinizde yararlıdır. Örneğin, uygulama, kullanıcının görüntülenecek tablonun adını belirtmesini sağlayabilir. Veri kaynağının tasarım zamanında bulunmadığı durumlarda da gereklidir. Bu, diziler, koleksiyonlar, türsüz veri kümeleri ve veri okuyucuları gibi veri kaynaklarını içerir.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGrid> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md). Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetimi **araç kutusunda** varsayılan olarak değildir. Ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: öğeleri ekleme araç kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Ayrıca, Visual Studio 2005 ' de tasarım zamanı veri bağlama için **veri kaynakları** penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da verileri denetimlere bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>DataGrid denetimini tasarımcıda tek bir tabloya veri bağlamak için

1. Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini, bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.

2. Veri kaynağı bir veri kümesi ise, <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini bağlanacak tablonun adı olarak ayarlayın.

3. Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.

     Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır. Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle bir veri bağdaştırıcısının `Fill` yöntemini, aşağıdaki kod örneğinde olduğu gibi, `DsCategories1`olarak adlandırılan bir veri kümesini dolduran şekilde çağırır:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. Seçim Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin.

     Tablo stili yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ile ve tüm sütunları görünür olur.

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>DataGrid denetimini tasarımcıda veri kümesindeki birden çok tabloya bağlamak için

1. Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini, bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.

2. Veri kümesi ilgili tabloları içeriyorsa (yani bir ilişki nesnesi içeriyorsa) <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini üst tablonun adı olarak ayarlayın.

3. Veri kümesini dolduracak kodu yazın.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Visual Studio'da verilere erişime](/visualstudio/data-tools/accessing-data-in-visual-studio)
