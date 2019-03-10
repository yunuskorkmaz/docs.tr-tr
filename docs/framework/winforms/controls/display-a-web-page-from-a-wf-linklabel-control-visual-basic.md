---
title: 'Nasıl yapılır: Bir Windows Forms LinkLabel denetiminden (Visual Basic) Web sayfası görüntüleme'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 7e80dba9cd43385be016506ac2a7e887a68dedf2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705239"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Nasıl yapılır: Bir Windows Forms LinkLabel denetiminden (Visual Basic) Web sayfası görüntüleme
Bir kullanıcı bir Windows Forms tıkladığında bu örnek bir Web sayfası varsayılan tarayıcıda görüntülenir. <xref:System.Windows.Forms.LinkLabel> denetimi.  
  
## <a name="example"></a>Örnek  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Adlı bir Windows formu `Form1`.  
  
-   A <xref:System.Windows.Forms.LinkLabel> adlı Denetim `LinkLabel1`.  
  
-   Etkin bir Internet bağlantısı.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Çağrı <xref:System.Diagnostics.Process.Start%2A> yöntemi tam güven gerektirir. Daha fazla bilgi için bkz. <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel Denetimi](linklabel-control-windows-forms.md)
