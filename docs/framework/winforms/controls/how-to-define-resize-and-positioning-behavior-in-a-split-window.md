---
title: 'Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328679"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama
Bölmelerden <xref:System.Windows.Forms.SplitContainer> denetim kiralamak kendileri de olmak için yeniden boyutlandırılabilir ve kullanıcılar tarafından yönetilebilir. Ancak, olacaktır istediğinizde Bölümlendirici programlı olarak denetlemek için bir kez — burada yer alır ve ne derece taşınabilir.  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği ve diğer özellikleri <xref:System.Windows.Forms.SplitContainer> denetim gereksinimlerinize uyacak şekilde, kullanıcı arabiriminin davranışı üzerinde kesin denetim verir. Bu özellikler aşağıdaki tabloda listelenmiştir.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Özelliği|Bölümlendirici klavye veya fare yoluyla taşınabilir olup olmadığını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Özelliği|Taşınabilir ayırıcıyı için sol veya üst kenarından piksel cinsinden uzaklığı belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği|Bölümlendirici kullanıcı tarafından taşınabilir piksel cinsinden en düşük bir uzaklık belirler.|  
  
 Aşağıdaki örnekte değiştirir <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliği bir "Bölücü Yaslama" etkisi; oluşturmak için bir kullanıcı bir ayırıcıyı sürüklediğinde, 1 varsayılan değer yerine 10 piksel birimleri cinsinden artırır.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>SplitContainer yeniden boyutlandırma davranışını tanımlamak için  
  
1. Bir yordamda <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliğini istenen boyut, böylece ayırıcı 'Yaslama' davranışını elde edilir.  
  
     Aşağıdaki kod örneğinde, formun içinde <xref:System.Windows.Forms.Form.Load> olay, bölümlendirici içinde <xref:System.Windows.Forms.SplitContainer> denetim sürüklendiğinde 10 piksel atlamak için ayarlanır.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     (Visual C#) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Bölümlendirici biraz sola veya sağa hareket anlaşılabilir etkisi olmayacak; Ancak, fare işaretçisini herhangi bir yönde 10 piksel gittiğinde, bölümlendirici yeni konumuna yaslanacak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
