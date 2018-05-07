---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme'
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
ms.openlocfilehash: ffcb84059dfceb85cdb347c3ddf1b80ab96c2aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Farklı renkler için çeşitli kısımlarını uygulayarak bir <xref:System.Windows.Forms.DataGrid> denetim bilgileri okumak ve yorumlamak kolaylaştırmak için yardımcı olabilir. Renk satırlara ve sütunlara uygulanabilir. Satırları ve sütunları da gizlenebilir veya kümeleri gösterilmektedir.  
  
 Biçimlendirme üç temel nokta <xref:System.Windows.Forms.DataGrid> denetim. Verilerin görüntülendiği varsayılan stilini kurmak için özellikleri ayarlayabilirsiniz. Bu taban, belirli tabloları çalışma zamanında görüntülenme biçimini özelleştirebilirsiniz. Son olarak, hangi sütunların renkleri yanı sıra veri kılavuzu görüntülenen değiştirebilir ve diğer biçimlendirme gösterilir.  
  
 Veri Kılavuzu biçimlendirme bir ilk adım, özellikleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid> kendisi. Bu renk ve biçime seçimler, ardından veri tabloları ve sütunları görüntülenen bağlı olarak değişiklik yapabilirsiniz bir temel oluşturur.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için varsayılan stil oluşturmak için  
  
1.  Aşağıdaki özellikleri uygun şekilde ayarlayın:  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Özelliği ızgaranın sayılı satırların rengi tanımlar. Ayarladığınızda <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliği için farklı bir renk, her bir satır ayarlanmış bu yeni renge (satırları 1, 3, 5 ve benzeri).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Izgaranın sayılı satırların arka plan rengi (satırları 0, 2, 4, 6 ve benzeri).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Oysa <xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri ızgara satırların rengini belirler <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği, kılavuzun altına kaydırılan veya birkaç satır içerdiği yalnızca görülebilir nonrow alanının rengini belirler Kılavuzu.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Izgaranın kenarlık stili, aşağıdakilerden birini <xref:System.Windows.Forms.BorderStyle> numaralandırma değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Hemen kılavuz görüntülenen kılavuz penceresinin başlık arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Izgaranın üst başlık yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Izgaranın penceresinin başlık arka plan rengi.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzda metni görüntülemek için kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri Kılavuzu satırlardaki verileri tarafından görüntülenen yazı tipi rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri Kılavuzu kılavuz çizgilerinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Kılavuz birini hücrelerinin ayırarak çizgi stilini <xref:System.Windows.Forms.DataGridLineStyle> numaralandırma değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üstbilgilerini arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun üst bilgileri için kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kılavuz sütun başlıklarını sütunu üstbilgi metni ve (birden fazla ilgili tablo görüntülendiğinde satırları genişletmek için) artı/eksi karakterleri dahil olmak üzere, ön plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Alt tablolar, ilişki adı ve benzeri bağlantılar dahil olmak üzere veri kılavuzunda tüm bağlantıların metnin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Bir alt tabloda üst satırların arka plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Bir alt tabloda üst satırların ön plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adlarını yoluyla üst satırda görüntülenip görüntülenmediğini belirler <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırması.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Kılavuz sütunu varsayılan genişliğini (piksel cinsinden). Sıfırlamadan önce bu özelliği ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı ayrı aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), ya da özelliğinin hiçbir etkisi olmaz.<br /><br /> Özelliği 0'dan daha düşük bir değere ayarlanamıyor.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Izgaradaki satırların (piksel cinsinden) satır yüksekliği. Sıfırlamadan önce bu özelliği ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı ayrı aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), ya da özelliğinin hiçbir etkisi olmaz.<br /><br /> Özelliği 0'dan daha düşük bir değere ayarlanamıyor.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Izgaranın satır üstbilgilerinin genişliği.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bir satır veya hücre seçildiğinde, arka plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bir satır veya hücre seçildiğinde, ön plan rengini budur.|  
  
    > [!NOTE]
    >  Denetimi zayıf renk seçim (örneğin, kırmızı ve yeşil) nedeniyle erişilemez hale da mümkündür denetimlerin renkleri özelleştirirken unutmayın. Kullanılabilir renklerini kullan **sistem renkleri** bu sorunu önlemek için palet.  
  
     Aşağıdaki yordamlar formunuz olduğunu varsayalım bir <xref:System.Windows.Forms.DataGrid> denetimine bağlı bir veri tablosuna. Daha fazla bilgi için bkz: [Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Veri tablosu tablo ve sütun stilini programlı olarak ayarlamak için  
  
1.  Yeni tablo stili oluşturun ve özelliklerini ayarlayın.  
  
2.  Bir sütun stili oluşturun ve özelliklerini ayarlayın.  
  
3.  Sütun stili tablo stili 's sütun stilleri koleksiyonuna ekleyin.  
  
4.  Tablo Stili veri kılavuzunun tablo stilleri koleksiyona ekleyin.  
  
5.  Aşağıdaki örnekte, yeni bir örneğini oluşturmak <xref:System.Windows.Forms.DataGridTableStyle> ve kendi <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği.  
  
6.  Yeni bir örneğini oluşturmak bir **GridColumnStyle** ve kendi **MappingName** (ve diğer bazı düzeni ve görüntü özelliklerini).  
  
7.  Oluşturmak istediğiniz her sütun stili için 2 ile 6 arasındaki adımları yineleyin.  
  
     Aşağıdaki örnek gösterilmektedir nasıl bir <xref:System.Windows.Forms.DataGridTextBoxColumn> sütunda görüntülenecek bir ad olduğu için oluşturulur. Ayrıca, sütun stili eklemek <xref:System.Windows.Forms.GridColumnStylesCollection> tablo stili ve tablo stiline ekleyin <xref:System.Windows.Forms.GridTableStylesCollection> veri kılavuzunun.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
