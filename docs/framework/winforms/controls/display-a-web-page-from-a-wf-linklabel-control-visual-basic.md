---
title: LinkLabel denetiminden Web sayfasını görüntüle (Visual Basic)
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
ms.openlocfilehash: 75373d55b7bc5ef11e39d5b9546996cb1c4f6f7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745921"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Nasıl yapılır: Bir Windows Forms LinkLabel Denetiminden Web Sayfası Görüntüleme (Visual Basic)
Bu örnek, Kullanıcı Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimine tıkladığında varsayılan tarayıcıda bir Web sayfası görüntüler.  
  
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
 Bu örnek şunları gerektirir:  
  
- `Form1`adlı bir Windows formu.  
  
- `LinkLabel1`adlı <xref:System.Windows.Forms.LinkLabel> denetim.  
  
- Etkin bir Internet bağlantısı.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.Diagnostics.Process.Start%2A> yöntemine yapılan çağrı tam güven gerektirir. Daha fazla bilgi için bkz. <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel Denetimi](linklabel-control-windows-forms.md)
