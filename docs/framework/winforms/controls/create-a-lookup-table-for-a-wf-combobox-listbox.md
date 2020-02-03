---
title: ComboBox, ListBox veya CheckedListBox denetimi için arama tablosu oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737375"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma
Bazen, verileri bir Windows form üzerinde Kullanıcı dostu bir biçimde göstermek yararlıdır, ancak verileri programınıza daha anlamlı bir biçimde depolar. Örneğin, yiyecek için bir sipariş formu, menü öğelerini bir liste kutusunda ada göre görüntüleyebilir. Ancak, siparişi kaydeden veri tablosu, yiyecek 'yi temsil eden benzersiz KIMLIK numaralarını içerir. Aşağıdaki tablolarda, yiyecek için sipariş formu verilerinin nasıl depolandığı ve görüntüleneceği bir örnek gösterilmektedir.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|Sipariş|ID|Miktar|  
|-------------|------------|--------------|  
|4085|12|1\.|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|Kimlik|Ad|  
|--------|----------|  
|12|Patates|  
|13|Tavuk|  
  
 Bu senaryoda, **OrderDetailsTable**adlı bir tablo, görüntüleme ve kaydetme konusunda endişe ettiğiniz gerçek bilgileri depolar. Ancak, alan kazanmak için oldukça şifreli bir biçimde olur. Diğer tablo, **ItemTable**, yalnızca hangi kimlik numarasının hangi yiyecek adına eşdeğer olduğu ve gerçek yiyecek siparişleriyle ilgili hiçbir şey hakkındaki görünümle ilgili bilgileri içerir.  
  
 **ItemTable** , üç özellik aracılığıyla <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>veya <xref:System.Windows.Forms.CheckedListBox> denetimine bağlanır. `DataSource` özelliği bu tablonun adını içerir. `DisplayMember` özelliği, denetimde göstermek istediğiniz tablonun veri sütununu içerir (yiyecek adı). `ValueMember` özelliği, depolanan bilgiler (KIMLIK numarası) ile ilgili tablonun veri sütununu içerir.  
  
 **OrderDetailsTable** , <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğinden erişilen bağlama koleksiyonuyla denetime bağlanır. Koleksiyona bir bağlama nesnesi eklediğinizde, bir denetim özelliğini bir veri kaynağındaki belirli bir veri üyesine (KIMLIK numaraları sütunu) bağladığınızda ( **OrderDetailsTable**). Denetimde bir seçim yapıldığında bu tablo, form girişinin kaydedildiği yerdir.  
  
### <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturmak için  
  
1. Forma <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>veya <xref:System.Windows.Forms.CheckedListBox> denetimi ekleyin.  
  
2. Veri kaynağınıza bağlanın.  
  
3. İki tablo arasında bir veri ilişkisi oluşturun. Bkz. [DataRelation nesnelerine giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).  
  
4. Aşağıdaki özellikleri ayarlayın. Bunlar kodda veya tasarımcıda ayarlanabilir.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Hangi KIMLIK numarasının hangi öğe ile eşdeğer olduğunu belirten bilgi içeren tablo. Önceki senaryoda bu `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Denetimde görüntülenmesini istediğiniz veri kaynağı tablosunun sütunu. Önceki senaryoda bu `"Name"` (kod içinde ayarlamak için tırnak işaretleri kullanın).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Depolanan bilgileri içeren veri kaynağı tablosunun sütunu. Önceki senaryoda bu `"ID"` (kod içinde ayarlamak için tırnak işaretleri kullanın).|  
  
5. Yordamda, denetimin <xref:System.Windows.Forms.ListControl.SelectedValue%2A> özelliğini form girişini kaydeden tabloya bağlamak için <xref:System.Windows.Forms.ControlBindingsCollection> sınıfının <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemini çağırın. Ayrıca, **Özellikler** penceresindeki denetimin <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğine erişerek bunu kod yerine tasarımcıda de yapabilirsiniz. Önceki senaryoda bu `OrderDetailsTable`ve sütun `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve Windows Forms](../data-binding-and-windows-forms.md)
- [ListBox Denetimine Genel Bakış](listbox-control-overview-windows-forms.md)
- [ComboBox Denetimine Genel Bakış](combobox-control-overview-windows-forms.md)
- [CheckedListBox Denetimine Genel Bakış](checkedlistbox-control-overview-windows-forms.md)
- [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](windows-forms-controls-used-to-list-options.md)
