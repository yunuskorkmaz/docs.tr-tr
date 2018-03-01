---
title: "Nasıl yapılır: Bir Windows Forms LinkLabel Denetiminden Web Sayfası Görüntüleme (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ba5ba3b29bab148087e0f8b80b3f1c43aa74e761
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Nasıl yapılır: Bir Windows Forms LinkLabel Denetiminden Web Sayfası Görüntüleme (Visual Basic)
Bir kullanıcı bir Windows Forms tıkladığında bu örnek bir Web sayfasında varsayılan tarayıcıda görüntüler. <xref:System.Windows.Forms.LinkLabel> denetim.  
  
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
 Çağrı <xref:System.Diagnostics.Process.Start%2A> yöntemi, tam güven gerektirir. Daha fazla bilgi için bkz. <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.LinkLabel>  
 [LinkLabel Denetimi](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
