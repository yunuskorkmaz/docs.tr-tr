---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama'
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
ms.openlocfilehash: 665a1af990aaf615c763c1c2eae508024d9de5c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917821"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır. Denetimi tasarım zamanında, <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırarak çalışma zamanında bağlarsınız. Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.

 Veri kaynağı tasarım zamanında kullanılabiliyorsa — Örneğin, form bir veri kümesinin veya bir veri görünümünün örneğini içeriyorsa — tasarım zamanında Kılavuzu veri kaynağına bağlayabilirsiniz. Ardından, verilerin kılavuzda nasıl görüneceğine ilişkin önizleme yapabilirsiniz.

 Ayrıca, çalışma zamanında Kılavuzu programlı bir şekilde bağlayabilirsiniz. Bu, çalışma zamanında aldığınız bilgilere göre bir veri kaynağı ayarlamak istediğinizde yararlıdır. Örneğin, uygulama, kullanıcının görüntülenecek tablonun adını belirtmesini sağlayabilir. Veri kaynağının tasarım zamanında bulunmadığı durumlarda da gereklidir. Bu, diziler, koleksiyonlar, türsüz veri kümeleri ve veri okuyucuları gibi veri kaynaklarını içerir.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGrid> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin. Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetim **araç kutusunda** varsayılan olarak değildir. Ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Araç kutusuna](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))öğe ekleyin. Ayrıca, Visual Studio 2005 ' de tasarım zamanı veri bağlama için **veri kaynakları** penceresini kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da verileri denetimlere bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>DataGrid denetimini tasarımcıda tek bir tabloya veri bağlamak için

1. Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.

2. Veri kaynağı bir veri kümesi ise, <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliği bağlanacak tablonun adına ayarlayın.

3. Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.

     Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır. Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle bir veri bağdaştırıcısının `Fill` yöntemini, aşağıdaki kod örneğinde olduğu gibi, adlı `DsCategories1`bir veri kümesini dolduran şekilde çağırabilirsiniz:

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

1. Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.

2. Veri kümesi ilgili tabloları içeriyorsa (yani bir ilişki nesnesi içeriyorsa), <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliği üst tablonun adı olarak ayarlayın.

3. Veri kümesini dolduracak kodu yazın.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Visual Studio'da verilere erişime](/visualstudio/data-tools/accessing-data-in-visual-studio)
