---
title: DataGrid denetimini biçimlendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 30342a89f3176255fa7217ccbbbd91c166ff7f35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732965"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGrid> denetiminin çeşitli bölümlerine farklı renkler uygulamak, bilgilerin okunmasını ve yorumlanması daha kolay hale getirmenize yardımcı olabilir. Renk, satırlara ve sütunlara uygulanabilir. Satırlar ve sütunlar da gizlenebilir veya sizin için de görünür.  
  
 <xref:System.Windows.Forms.DataGrid> denetimini biçimlendirmenin üç temel yönü vardır. Özellikleri, verilerin görüntülendiği varsayılan bir stil oluşturmak için ayarlayabilirsiniz. Bu temelden, belirli tabloların çalışma zamanında görüntülenme şeklini özelleştirebilirsiniz. Son olarak, veri kılavuzunda görüntülenecek sütunları ve gösterilen renkleri ve diğer biçimlendirmeleri değiştirebilirsiniz.  
  
 Bir veri kılavuzunu biçimlendirirken ilk adım olarak, <xref:System.Windows.Forms.DataGrid> özelliklerini ayarlayabilirsiniz. Bu renk ve biçim seçimleri, daha sonra görünen veri tablolarına ve sütunlara göre değişiklik yapabileceğiniz bir temel oluşturur.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için varsayılan bir stil oluşturmak için  
  
1. Aşağıdaki özellikleri uygun şekilde ayarlayın:  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> özelliği, kılavuzun çift sayılı satırlarının rengini tanımlar. <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliğini farklı bir renge ayarladığınızda, diğer her satır bu yeni renge ayarlanır (satır 1, 3, 5, vb.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kılavuzun çift sayılı satırlarının arka plan rengi (satırlar 0, 2, 4, 6, vb.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri kılavuzdaki satırların rengini belirlerse, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği yalnızca ızgara en alta kaydırıldığında veya kılavuzda yalnızca birkaç satır mevcutsa görünür olan satır olmayan alanın rengini belirler.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<xref:System.Windows.Forms.BorderStyle> sabit listesi değerlerinden biri olan kılavuzun kenarlık stili.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kılavuzun hemen üstünde görünen kılavuzun pencere açıklamalı arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Kılavuzun üst kısmındaki başlık yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kılavuzun pencere açıklamalı arka plan rengi.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzdaki metni göstermek için kullanılan yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri kılavuzu satırlarındaki veriler tarafından gösterilecek yazı tipi rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri kılavuzunun kılavuz çizgilerinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<xref:System.Windows.Forms.DataGridLineStyle> sabit listesi değerlerinden biri olan kılavuzun hücrelerini ayıran çizgilerin stili.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üst bilgilerinin arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun başlıkları için kullanılan yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kılavuzun sütun üstbilgilerinin, sütun üst bilgisi metni ve artı/eksi glifleri (birden çok ilişkili tablo görüntülenirken satırları genişletmek için) dahil ön plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Veri kılavuzundaki tüm bağlantıların, alt tablolara bağlantılar, ilişki adı vb. gibi tüm bağlantıların metin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Alt tabloda, bu, üst satırların arka plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Alt tabloda, bu, üst satırların ön plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adlarının, <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırması aracılığıyla üst satırda görüntülenip görüntülenmeyeceğini belirler.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Kılavuzdaki sütunların varsayılan genişliği (piksel cinsinden). <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini sıfırlamadan önce (ayrı olarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi aracılığıyla) bu özelliği ayarlayın, ya da özelliğin hiçbir etkisi olmayacaktır.<br /><br /> Özellik 0 ' dan küçük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Kılavuzdaki satırların satır yüksekliği (piksel cinsinden). <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini sıfırlamadan önce (ayrı olarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi aracılığıyla) bu özelliği ayarlayın, ya da özelliğin hiçbir etkisi olmayacaktır.<br /><br /> Özellik 0 ' dan küçük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Kılavuzun satır üst bilgilerinin genişliği.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bir satır veya hücre seçildiğinde, bu arka plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bir satır veya hücre seçildiğinde bu, ön plan rengidir.|  
  
    > [!NOTE]
    > Denetimlerin renklerini özelleştirirken, kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle denetimi erişilemez hale getirmek mümkün olduğunca göz önünde bulundurun. Bu sorundan kaçınmak için **sistem renkleri** paletindeki kullanılabilir renkleri kullanın.  
  
     Aşağıdaki yordamlarda formunuzun bir veri tablosuna göre <xref:System.Windows.Forms.DataGrid> denetimi olduğu varsayılır. Daha fazla bilgi için, bkz. [Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Bir veri tablosunun tablo ve sütun stilini programlı bir şekilde ayarlamak için  
  
1. Yeni bir tablo stili oluşturun ve özelliklerini ayarlayın.  
  
2. Sütun stili oluşturun ve özelliklerini ayarlayın.  
  
3. Sütun stilini tablo stilinin sütun stilleri koleksiyonuna ekleyin.  
  
4. Tablo stilini veri kılavuzunun tablo stilleri koleksiyonuna ekleyin.  
  
5. Aşağıdaki örnekte, yeni bir <xref:System.Windows.Forms.DataGridTableStyle> örneği oluşturun ve <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğini ayarlayın.  
  
6. Bir **GridColumnStyle** 'ın yeni bir örneğini oluşturun ve onun **MappingName** değerini (ve diğer düzen ve görüntü özelliklerini) ayarlayın.  
  
7. Oluşturmak istediğiniz her sütun stili için 2 ile 6 arasındaki adımları yineleyin.  
  
     Aşağıdaki örnek, sütununda bir ad görüntülenecek şekilde bir <xref:System.Windows.Forms.DataGridTextBoxColumn> nasıl oluşturulduğunu gösterir. Ayrıca, sütun stilini tablo stilinin <xref:System.Windows.Forms.GridColumnStylesCollection> eklersiniz ve tablo stilini veri kılavuzunun <xref:System.Windows.Forms.GridTableStylesCollection> eklersiniz.  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
