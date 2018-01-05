---
title: "Nasıl yapılır: MDI Alt Formlarını Düzenleme"
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
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a0a32f6a97e02db8e395db504f36bb5270b195c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-arrange-mdi-child-forms"></a>Nasıl yapılır: MDI Alt Formlarını Düzenleme
Genellikle, uygulamaları kutucuğu, Cascade ve Yerleştir, açık MDI alt formları düzenini denetleyen gibi eylemleri menü komutlarını sahip olur. Kullanabileceğiniz <xref:System.Windows.Forms.Form.LayoutMdi%2A> biriyle yöntemi <xref:System.Windows.Forms.MdiLayout> MDI alt formları yeniden düzenlemek için numaralandırma değerlerinin ana formu.  
  
 <xref:System.Windows.Forms.MdiLayout> Numaralandırma değerlerinin görüntü alt formları, yatay veya dikey olarak döşenir gibi basamaklı olarak ya da MDI Formu alt kısmı düzenlenmiş alt form simgeler. Bu değerleri Windows komutları aynı etkiye sahip **basamaklı windows**, **windows yan yana göster**, **Göster Yığılmış windows**, ve **masaüstünü gösterir** sırasıyla.  
  
 Genellikle, bu yöntemleri menü öğesinin tarafından çağrılan olay işleyicileri olarak kullanılan <xref:System.Windows.Forms.Control.Click> olay. Bu şekilde, bir menü öğesi "Pencereleri Basamakla" metni ile MDI alt pencereleri istenen etkisi olabilir.  
  
### <a name="to-arrange-child-forms"></a>Alt formlar düzenlemek için  
  
1.  Bir yöntem kullanmak <xref:System.Windows.Forms.Form.LayoutMdi%2A> ayarlamak için yöntemin <xref:System.Windows.Forms.MdiLayout> MDI üst form için numaralandırması. Aşağıdaki örnek kullanır <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> MDI üst formun alt windows için numaralandırma değeri (`Form1`). Numaralandırma sırasında olay işleyicisi için kod içinde kullanılan <xref:System.Windows.Forms.Control.Click> olayı **Pencereleri Basamakla** menü öğesi.  
  
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
    >  Aynı zamanda windows ve düzenleyerek windows simgeler olarak değiştirerek döşeme <xref:System.Windows.Forms.MdiLayout> numaralandırma değeri kullanılır.  
  
2.  Visual C# kullanıyorsanız aşağıdaki kodu olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: MDI Alt Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
