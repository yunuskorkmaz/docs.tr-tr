---
title: 'Nasıl yapılır: MDI Alt Formlarını Düzenleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955112"
---
# <a name="how-to-arrange-mdi-child-forms"></a>Nasıl yapılır: MDI Alt Formlarını Düzenleme
Genellikle, uygulamalar, açık MDI alt formlarının yerleşimini denetleyen kutucuk, basamakla ve Düzenle gibi eylemler için menü komutlarına sahip olur. Bir MDI parent formundaki <xref:System.Windows.Forms.Form.LayoutMdi%2A> alt formları yeniden düzenlemek için <xref:System.Windows.Forms.MdiLayout> bir numaralandırma değerlerinden biriyle yöntemini kullanabilirsiniz.  
  
 <xref:System.Windows.Forms.MdiLayout> Sabit listesi değerleri, alt formları yatay veya dikey döşeli olarak basamaklı olarak ya da MDI formunun alt bölümü üzerinde düzenlenmiş alt form simgeleri olarak görüntüler. Bu değerler, Windows komutları **basamaklı pencereleri**ile aynı etkiye sahiptir, **pencereleri yan yana gösterir**, Windows 'u **yığılmış**ve sırasıyla **Masaüstünü gösterir**.  
  
 Genellikle, bu yöntemler bir menü öğesinin <xref:System.Windows.Forms.Control.Click> olayı tarafından çağrılan olay işleyicileri olarak kullanılır. Bu şekilde, "Cascade Windows" metnini içeren bir menü öğesi, MDI alt pencereleri üzerinde istenen etkiye sahip olabilir.  
  
### <a name="to-arrange-child-forms"></a>Alt formları düzenlemek için  
  
1. Bir yönteminde, MDI parent form <xref:System.Windows.Forms.Form.LayoutMdi%2A> için <xref:System.Windows.Forms.MdiLayout> sabit listesini ayarlamak için yöntemini kullanın. Aşağıdaki örnek, MDI parent <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> form (`Form1`) öğesinin alt pencereleri için numaralandırma değeri kullanır. Sabit listesi, <xref:System.Windows.Forms.Control.Click> **Cascade Windows** menü öğesi olayı için olay işleyicisi sırasında kodda kullanılır.  
  
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
    > Ayrıca, <xref:System.Windows.Forms.MdiLayout> kullanılan sabit listesi değerini değiştirerek pencereleri de döşeyerek simgeler olarak düzenleyebilirsiniz.  
  
2. Görsel C#kullanıyorsanız, olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu koyun.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çok Belgeli Arabirim (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI üst formları oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI alt formları oluşturma](how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI alt öğesini belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI alt öğesine veri gönderme](how-to-send-data-to-the-active-mdi-child.md)
