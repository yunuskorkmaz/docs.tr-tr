---
title: "Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f49a8fbd2cc8ffae94e4dcbbc4babf7c1137cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Nasıl yapılır: Bir Windows Forms ComboBox, ListBox veya CheckedListBox Denetimi için Arama Tablosu Oluşturma
Bazen kullanımı kolay bir biçimde bir Windows formunda veri görüntüleme, ancak veri programınıza daha anlamlı bir biçimde depolamak kullanışlıdır. Örneğin, bir sipariş formu Yemek için bir liste kutusunda ada göre menü öğelerini görüntüleyebilir. Ancak, sipariş kaydı veri tablosu yemek temsil eden benzersiz kimlik numaraları içerecektir. Aşağıdaki tablolarda, depolamak ve Yemek Sipariş formu verileri görüntülemek nasıl bir örneği gösterilmektedir.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|Öğe kimliği|Miktar|  
|-------------|------------|--------------|  
|4085|12|1.|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|Kimlik|Ad|  
|--------|----------|  
|12|Patates|  
|13|Tavuk|  
  
 Bu senaryoda, bir tablo **OrderDetailsTable**, kaydetme ve görüntüleme ile ilgili gerçek bilgileri depolar. Ancak alanı kaydetmek için bunu oldukça şifreli biçimde yapar. Diğer tablo **ItemTable**, hangi kimliği hakkında sayıdır hangi yemek adına ve gerçek yemek siparişler hakkında hiçbir şey eşdeğer yalnızca görünüm ilgili bilgiler içerir.  
  
 **ItemTable** bağlı <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, veya <xref:System.Windows.Forms.CheckedListBox> denetim üç özellik aracılığıyla. `DataSource` Özelliği, bu tablonun adını içerir. `DisplayMember` Özelliği (yemek adı) denetiminde görüntülemek istediğiniz bu tablonun veri sütunu içerir. `ValueMember` Özelliği (kimlik numarası) depolanmış bilgilerle bu tablonun veri sütunu içerir.  
  
 **OrderDetailsTable** üzerinden erişilen kendi bağlamaları koleksiyonu tarafından denetime bağlı <xref:System.Windows.Forms.Control.DataBindings%2A> özelliği. Koleksiyona bir bağlama nesnesi eklediğinizde, denetim özelliğini bir veri kaynağındaki belirli veri üyesini (kimlik numaraları sütun) bağlandığınız ( **OrderDetailsTable**). Denetimde bir seçim yapıldığında, bu form girişi kaydedildiği tablodur.  
  
### <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturmak için  
  
1.  Ekleme bir <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, veya <xref:System.Windows.Forms.CheckedListBox> forma denetim.  
  
2.  Veri kaynağına bağlanın.  
  
3.  İki tablo arasında veri ilişkisi oluşturun. Bkz: [DataRelation nesnelerine giriş](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Aşağıdaki özellikleri ayarlayın. Bunlar, kod veya tasarımcı ayarlanabilir.  
  
    |Özellik|Ayar|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Hangi kimliği hakkında hangi öğeye eşdeğer sayıdır bilgi içeren tablo. Önceki senaryoda budur `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Denetimde görüntülemek istediğiniz veri kaynağı tablosuna sütun. Önceki senaryoda budur `"Name"` (kodda ayarlamak için tırnak işaretleri kullanın).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Depolanan bilgiler içeren veri kaynağı tablo sütun. Önceki senaryoda budur `"ID"` (kodda ayarlamak için tırnak işaretleri kullanın).|  
  
5.  Bir yordamda çağrısı <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ControlBindingsCollection> denetimin bağlamak için sınıf <xref:System.Windows.Forms.ListControl.SelectedValue%2A> form girişi kaydı tabloya özelliği. Ayrıca, kodda yerine tasarımcısında denetimin erişerek bunu yapabilirsiniz <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğinde **özellikleri** penceresi. Önceki senaryoda budur `OrderDetailsTable`, ve sütun `"ItemID"`.  
  
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
