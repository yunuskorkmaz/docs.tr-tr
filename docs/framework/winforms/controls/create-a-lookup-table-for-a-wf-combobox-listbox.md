---
title: 'Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma'
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
ms.openlocfilehash: b719f2112aac1292b668fe199d48de4b0b60ed21
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773097"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma
Bazen bir Windows Form üzerinde kolay bir biçimde verileri görüntüler ancak programınız için daha anlamlı bir biçimde verileri depolamak kullanışlıdır. Örneğin, bir sipariş formu Gıda için bir liste kutusunda ad olarak menü öğeleri görüntülenebilir. Ancak, siparişin kaydı veri tablosu Gıda temsil eden benzersiz kimlik numaraları içerecektir. Aşağıdaki tablolarda, depolamak ve yemek siparişi biçimli verileri görüntülemek nasıl bir örnek gösterilmektedir.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|Sipariş Kimliği|öğe kimliği|Miktar|  
|-------------|------------|--------------|  
|4085|12|1.|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|Kimlik|Ad|  
|--------|----------|  
|12|Patates|  
|13|Tavuk|  
  
 Bu senaryoda, bir tablo **OrderDetailsTable**, kaydetme ve görüntüleme ile ilgili gerçek bilgileri depolar. Ancak, alandan kazanmak için bunu oldukça şifreli biçimde yapar. Diğer bir tabloda **ItemTable**, hangi kimliği hakkında sayıdır hangi Gıda adına ve gerçek Gıda siparişler hakkında hiçbir şey eşdeğer yalnızca görünüm güvenlikle ilgili bilgiler içerir.  
  
 **ItemTable** bağlı <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, veya <xref:System.Windows.Forms.CheckedListBox> üç özellikleri aracılığıyla denetimi. `DataSource` Özelliği bu tablonun adını içerir. `DisplayMember` Özelliği, bu tablonun (Gıda adı) denetiminde görüntülemek istediğiniz veri sütunu içerir. `ValueMember` Özelliği, bu tablonun saklı bilgileri (kimlik numarası) ile veri sütunu içerir.  
  
 **OrderDetailsTable** aracılığıyla erişilen kendi bağlamaları koleksiyona göre denetimine bağlı <xref:System.Windows.Forms.Control.DataBindings%2A> özelliği. Koleksiyona bağlama nesnesi eklediğinizde, bir denetim özelliği bir veri kaynağındaki belirli veri üyesini (kimliği sayı sütununun) bağlandığınız ( **OrderDetailsTable**). Denetimdeki seçim yapıldığında, bu form girişi kaydedildiği tablodur.  
  
### <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturma  
  
1.  Ekleme bir <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, veya <xref:System.Windows.Forms.CheckedListBox> forma.  
  
2.  Veri kaynağınıza bağlayın.  
  
3.  İki tablo arasında bir veri ilişkisi oluşturur. Bkz: [DataRelation nesnelerine giriş](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Aşağıdaki özellikleri ayarlayın. Bunlar, kod veya tasarımcı ayarlanabilir.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Hangi kimliği numarasını hangi öğesine eşdeğerdir bilgilerini içeren tablo. Önceki senaryoda budur `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Denetiminde görüntülemek istediğiniz veri kaynağı tablosu içeren sütun. Önceki senaryoda budur `"Name"` (kodda ayarlamak için tırnak işaretleri kullanın).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Depolanan bilgiler içeren veri kaynağı tablosu içeren sütun. Önceki senaryoda budur `"ID"` (kodda ayarlamak için tırnak işaretleri kullanın).|  
  
5.  Bir yordamda çağrı <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ControlBindingsCollection> denetimin bağlamak için sınıf <xref:System.Windows.Forms.ListControl.SelectedValue%2A> özelliğini form girişi kayıt tablosu. Ayrıca, kodda yerine tasarımcısında denetimin erişerek bunu yapabilirsiniz <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğinde **özellikleri** penceresi. Önceki senaryoda budur `OrderDetailsTable`, ve sütun `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [ListBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [ComboBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
