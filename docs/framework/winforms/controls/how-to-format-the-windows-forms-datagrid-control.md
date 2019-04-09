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
ms.openlocfilehash: a07fde63463d209e0006de9be677636f19fd93a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147907"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Çeşitli bölümlerine farklı renkler uygulayarak bir <xref:System.Windows.Forms.DataGrid> denetim bilgileri içine okumak ve yorumlamak kolay hale getirmek için yardımcı olabilir. Satırları ve sütunları için renk uygulanabilir. Satırları ve sütunları da gizli veya gösterilen günlüklerinizin bekletilme.  
  
 Biçimlendirme üç temel unsur vardır <xref:System.Windows.Forms.DataGrid> denetimi. Verilerin görüntülendiği bir varsayılan stilde kurmak için özellikleri ayarlayabilirsiniz. Bu temelden belirli tablolar, çalışma zamanında görüntülenme biçimini özelleştirebilirsiniz. Son olarak, hangi sütunların renkleri yanı sıra veri kılavuzunda görüntülenen değiştirebilirsiniz ve diğer biçimlendirme gösterilir.  
  
 Bir ilk adım olarak, veri kılavuzu biçimlendirme özellikleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid> kendisi. Bu renk ve biçim seçimleri kendisinden sonra veri tabloları ve sütunları görüntülenen bağlı olarak değişiklik yapabilirsiniz bir temel oluşturur.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için bir varsayılan stilde oluşturmak için  
  
1.  Aşağıdaki özellikleri uygun şekilde ayarlayın:  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> Özelliği sayılı satır kılavuzunun rengini tanımlar. Ayarladığınızda <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliği farklı bir renge, her bir satır için bu yeni renk ayarlanır (satırlar 1, 3, 5 vb.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Izgaranın sayılı satırların arka plan rengi (0, 2, 4, 6 ve benzeri satır).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Oysa <xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri ızgara satır rengini belirler <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özellik Kılavuzu altına kaydırılan veya yalnızca birkaç satır içerdiği görülebilir nonrow alanının rengini belirler Kılavuz.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Izgaranın kenarlık stili, aşağıdakilerden birini <xref:System.Windows.Forms.BorderStyle> sabit listesi değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kılavuzun üzerindeki hemen görünen kılavuz pencere başlığı arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Kılavuz üst kısmındaki başlık yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Izgaranın pencere başlığı arka plan rengi.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzda metni görüntülemek için kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri Kılavuzu satırı verilerinde tarafından görüntülenen yazı tipi rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri Kılavuzu, kılavuz çizgilerinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Kılavuzun birini hücreleri ayıran çizgilerin stili <xref:System.Windows.Forms.DataGridLineStyle> sabit listesi değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üst bilgilerinin arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun üst bilgilerini kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kılavuz sütun üst bilgilerini sütunu üstbilgi metni ve (satır birden çok ilişkili tabloyla görüntülendiğinde genişletmek için) artı/eksi karakterleri dahil olmak üzere, ön plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Veri kılavuzunda alt tablolar, ilişki adı ve benzeri bağlantılar dahil olmak üzere tüm bağlantıların metnin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Bir alt tabloda üst satırların arka plan rengi budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Bir alt tabloda üst satırları ön plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adları üst satırın yoluyla görüntülenip görüntülenmediğini belirler <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> sabit listesi.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Izgara sütunları varsayılan genişliğini (piksel cinsinden). Sıfırlamadan önce bu özelliği ayarlayın <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı olarak aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), veya özellik hiçbir etkisi olmaz.<br /><br /> Özelliği, 0'dan düşük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Izgara satır satır yüksekliği (piksel cinsinden). Sıfırlamadan önce bu özelliği ayarlayın <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı olarak aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), veya özellik hiçbir etkisi olmaz.<br /><br /> Özelliği, 0'dan düşük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Izgaranın satır başlıklarında genişliği.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bu, bir satır veya hücre seçildiğinde, arka plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bu, bir satır veya hücre seçildiğinde, ön plan rengidir.|  
  
    > [!NOTE]
    >  Denetimler, denetimi kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle erişilemez hale getirmek mümkündür renklerini özelleştirirken göz önünde tutun. Kullanılabilir renklerini kullan **sistem renkleri** bu sorunu önlemek için palet.  
  
     Aşağıdaki yordamlar, formda olduğunu varsayalım. bir <xref:System.Windows.Forms.DataGrid> denetim bir veri tablosuna bağlı. Daha fazla bilgi için [Windows Forms DataGrid denetimini veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Tablo ve sütun bir veri tablosu stilini program üzerinden ayarlamak için  
  
1.  Yeni bir tablo stili oluşturun ve özelliklerini ayarlayın.  
  
2.  Sütun stil oluşturma ve özelliklerini ayarlayın.  
  
3.  Sütun stili tablo stili 's sütun stillerini koleksiyonuna ekleyin.  
  
4.  Tablo Stili veri kılavuzunun tablo stilleri koleksiyona ekleyin.  
  
5.  Aşağıdaki örnekte, yeni bir örneğini oluşturmak <xref:System.Windows.Forms.DataGridTableStyle> ve kendi <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği.  
  
6.  Yeni bir örneğini oluşturmak bir **GridColumnStyle** ve kendi **MappingName** (ve diğer bazı düzen ve görüntü özelliklerini).  
  
7.  Oluşturmak istediğiniz her bir sütun stili 2 ile 6 arasındaki adımları yineleyin.  
  
     Aşağıdaki örnekte nasıl bir <xref:System.Windows.Forms.DataGridTextBoxColumn> sütununda görüntülenecek bir ad olduğu için oluşturulur. Sütun stil ek olarak, eklediğiniz <xref:System.Windows.Forms.GridColumnStylesCollection> tablo stili ve tablo stili için eklediğiniz <xref:System.Windows.Forms.GridTableStylesCollection> veri kılavuzunun.  
  
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
