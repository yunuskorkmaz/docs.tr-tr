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
ms.openlocfilehash: 015e93fb551b8d48b8a57662b8def61c3cb46c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama
Bölmelerden <xref:System.Windows.Forms.SplitContainer> denetim ödünç kendilerini iyi duruma yeniden boyutlandırılabilir ve kullanıcılar tarafından yönetilebilir. Ancak, olacaktır istediğinizde Bölümlendirici programlı olarak denetlemek için kez — burada yer alır ve ne derece taşınabilmesi.  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği ve diğer özellikleri <xref:System.Windows.Forms.SplitContainer> denetim gereksinimlerinize uygun olarak, kullanıcı arabiriminizi davranışını üzerinde Tam Denetim verin. Bu özellikler aşağıdaki tabloda listelenmiştir.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Özelliği|Bölümlendirici klavye veya fare yoluyla taşınabilir olup olmadığını belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Özelliği|Taşınabilir Bölümlendirici çubuğuna sol veya üst kenarından piksel cinsinden uzaklığı belirler.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Özelliği|Bölümlendirici kullanıcı tarafından taşınabilmesi piksel cinsinden minimum uzaklığını belirler.|  
  
 Aşağıdaki örnek değiştirir <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> özelliği bir "Bölümlendirici tutturma" efekti; oluşturmak için kullanıcı Bölümlendirici sürüklendiğinde varsayılan 1 yerine 10 piksel birimlerinde artırır.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>SplitContainer yeniden boyutlandırma davranışını tanımlamak için  
  
1.  Bir yordamda ayarladığınız <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> istenen boyuta özelliğine böylece Bölümlendirici 'tutturma' davranışını elde edilir.  
  
     Aşağıdaki kod örneğinde, formun içinde <xref:System.Windows.Forms.Form.Load> olay, içinde Bölümlendirici <xref:System.Windows.Forms.SplitContainer> denetim sürüklendiğinde 10 piksel atlamak için ayarlanır.  
  
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
  
     Bölümlendirici biraz sola veya sağa hareket anlaşılabilir hiçbir etkisi olmaz; Ancak, fare işaretçisini herhangi bir yönde 10 piksel gittiğinde Bölümlendirici yeni konuma Daya.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
