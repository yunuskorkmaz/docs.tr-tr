---
title: Veri Grid Denetimini Biçimlendir
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
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182142"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGrid> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.DataGrid> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur. Daha fazla bilgi için [Bkz. Windows Formları DataGridView ve DataGrid Denetimleri arasındaki farklar.](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
  
 Denetimin <xref:System.Windows.Forms.DataGrid> çeşitli bölümlerine farklı renkler uygulamak, denetimdeki bilgilerin okunmasını ve yorumlanmasının kolay olmasına yardımcı olabilir. Renk satır lara ve sütunlara uygulanabilir. Satırlar ve sütunlar da gizlenebilir veya kendi takdirinize göre gösterilebilir.  
  
 Denetimi biçimlendirmenin <xref:System.Windows.Forms.DataGrid> üç temel yönü vardır. Verileri görüntülenen varsayılan stil oluşturacak şekilde özellikleri ayarlayabilirsiniz. Bu temelden, belirli tabloların çalışma zamanında görüntülenme şeklini özelleştirebilirsiniz. Son olarak, veri ızgarasında hangi sütunların görüntüleneceğini, renkleri ve gösterilen diğer biçimlendirmeyi değiştirebilirsiniz.  
  
 Veri ızgarasını biçimlendirmenin ilk adımı olarak, <xref:System.Windows.Forms.DataGrid> kendisinin özelliklerini ayarlayabilirsiniz. Bu renk ve biçim seçenekleri, görüntülenen veri tablolarına ve sütunlara bağlı olarak değişiklik yapabileceğiniz bir temel oluşturur.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için varsayılan bir stil oluşturmak için  
  
1. Aşağıdaki özellikleri uygun şekilde ayarlayın:  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Özellik, <xref:System.Windows.Forms.DataGrid.BackColor%2A> ızgaranın çift numaralı satırlarının rengini tanımlar. <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> Özelliği farklı bir renge ayarladığınızda, diğer her satır bu yeni renge ayarlanır (satır 1, 3, 5 ve benzeri).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Izgaranın çift numaralı satırlarının arka plan rengi (satırlar 0, 2, 4, 6 vb.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Kılavuzdaki <xref:System.Windows.Forms.DataGrid.BackColor%2A> satırların rengini ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri belirlerken, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özellik yalnızca ızgara alta kaydırıldığında veya ızgarada yalnızca birkaç satır bulunduğunda görülebilen satır dışı alanın rengini belirler.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Izgaranın kenarlık stili, <xref:System.Windows.Forms.BorderStyle> numaralandırma değerlerinden biri.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Izgaranın pencere yazısının arka plan rengi, ızgaranın hemen üzerinde görünür.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Kılavuz üst kısmında ki resim yazısı.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Izgaranın pencere yazısının arka plan rengi.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzdaki metni görüntülemek için kullanılan yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri ızgarası satırlarındaki veriler tarafından görüntülenen yazı tipinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri ızgarasının ızgara çizgilerinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Izgara hücrelerini ayıran çizgilerin stili, numaralandırma değerlerinden <xref:System.Windows.Forms.DataGridLineStyle> biri.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üstbilgilerinin arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun üstbilgisi için kullanılan yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Sütun üstbilgi metni ve artı/eksi glifler ilerler (birden çok ilgili tablo görüntülendiğinde satırları genişletmek için) dahil olmak üzere ızgara sütun üstbilgilerinin ön plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Alt tablolara bağlantılar, ilişki adı ve benzeri bağlantılar da dahil olmak üzere veri ızgarasındaki tüm bağlantıların metninin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Alt tabloda, bu üst satırların arka plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Alt tabloda, bu üst satırların ön plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adlarının üst satırda numaralandırma yoluyla <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> görüntülenip görüntülenmediğini belirler.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Kılavuzdaki sütunların varsayılan genişliği (piksel olarak). Bu özelliği <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ayrı ayrı veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntem yoluyla) sıfırlamadan önce ayarlayın, yoksa özelliğin hiçbir etkisi olmayacaktır.<br /><br /> Özellik 0'dan küçük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Kılavuzdaki satırların satır yüksekliği (piksel olarak). Bu özelliği <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ayrı ayrı veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntem yoluyla) sıfırlamadan önce ayarlayın, yoksa özelliğin hiçbir etkisi olmayacaktır.<br /><br /> Özellik 0'dan küçük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Izgaranın satır üstbilgilerinin genişliği.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bir satır veya hücre seçildiğinde, bu arka plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bir satır veya hücre seçildiğinde, bu ön plan rengidir.|  
  
    > [!NOTE]
    > Denetimlerin renklerini özelleştirirken, kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle denetimin erişilemez hale getirilmesinin mümkün olduğunu unutmayın. Bu sorunu önlemek için **Sistem Renkleri** paletinde bulunan renkleri kullanın.  
  
     Aşağıdaki yordamlar, formunuzun <xref:System.Windows.Forms.DataGrid> bir veri tablosuna bağlı bir denetimi olduğunu varsayar. Daha fazla bilgi için bkz: [Windows Formlar Veri Grid Denetimini Bir Veri Kaynağına Bağlama.](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Veri tablosunun tablo ve sütun stilini programlı olarak ayarlamak için  
  
1. Yeni bir tablo stili oluşturun ve özelliklerini ayarlayın.  
  
2. Sütun stili oluşturun ve özelliklerini ayarlayın.  
  
3. Sütun stilini tablo stilinin sütun stilleri koleksiyonuna ekleyin.  
  
4. Veri ızgarasının tablo stilleri koleksiyonuna tablo stilini ekleyin.  
  
5. Aşağıdaki örnekte, yeni <xref:System.Windows.Forms.DataGridTableStyle> bir örnek oluşturun <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> ve özelliğini ayarlayın.  
  
6. **GridColumnStyle'ın** yeni bir örneğini oluşturun ve **MappingName'ini** (ve diğer bazı düzen ve görüntü özelliklerini) ayarlayın.  
  
7. Oluşturmak istediğiniz her sütun stili için 2 ile 6 adımlarını yineleyin.  
  
     Sütunda bir ad <xref:System.Windows.Forms.DataGridTextBoxColumn> görüntüleneceği için aşağıdaki örnek, a'nın nasıl oluşturulduğunu göstermektedir. Ayrıca, sütun stilini tablo <xref:System.Windows.Forms.GridColumnStylesCollection> stiline eklersiniz ve tablo stilini <xref:System.Windows.Forms.GridTableStylesCollection> veri ızgarasına eklersiniz.  
  
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
