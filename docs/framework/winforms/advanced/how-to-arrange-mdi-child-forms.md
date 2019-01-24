---
title: 'Nasıl yapılır: MDI alt formlarını düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 6e1e4f22aa70d8ee4d4122f9e77427c101b6713f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540747"
---
# <a name="how-to-arrange-mdi-child-forms"></a>Nasıl yapılır: MDI alt formlarını düzenleme
Genellikle, kutucuk, Cascade ve düzenleme, açık MDI alt formlarını yerleşimini denetleyen gibi eylemleri menü komutlarını uygulamanız olacak. Kullanabileceğiniz <xref:System.Windows.Forms.Form.LayoutMdi%2A> yöntemi biriyle <xref:System.Windows.Forms.MdiLayout> numaralandırma değerlerinden bir MDI alt formları yeniden düzenlemek için ana formu.  
  
 <xref:System.Windows.Forms.MdiLayout> Numaralandırma değerlerinin görüntü alt formları basamaklı yatay veya dikey olarak döşenmiş gibi olarak ya da MDI formunun alt kısmı alt form simgeler olarak. Bu değerleri Windows komutları ile aynı etkiye sahip **basamaklı windows**, **windows yan yana göster**, **Göster Yığılmış windows**, ve **masaüstünü gösterir** sırasıyla.  
  
 Genellikle, bu yöntemler bir menü öğesinin tarafından çağrılan olay işleyicileri olarak kullanılan <xref:System.Windows.Forms.Control.Click> olay. Bu şekilde, bir menü öğesi metni "Cascade Windows" ile MDI alt pencereleri üzerinde istenen etkisi olabilir.  
  
### <a name="to-arrange-child-forms"></a>Alt formlarını düzenlemek için  
  
1.  Bir yöntem kullanmak <xref:System.Windows.Forms.Form.LayoutMdi%2A> ayarlanacak yöntemi <xref:System.Windows.Forms.MdiLayout> MDI üst formu için sabit listesi. Aşağıdaki örnekte <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> numaralandırma değeri MDI üst formunun alt pencereler için (`Form1`). Numaralandırma sırasında olay işleyicisi için kod içinde kullanılan <xref:System.Windows.Forms.Control.Click> olayı **Cascade Windows** menü öğesi.  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  Ayrıca windows ve windows düzenleyerek simgeler olarak değiştirerek döşeme <xref:System.Windows.Forms.MdiLayout> numaralandırma değeri kullanılır.  
  
2.  Visual kullanıyorsanız C#, formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI üst formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI alt formları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI alt öğesini belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI alt öğesine veri gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
