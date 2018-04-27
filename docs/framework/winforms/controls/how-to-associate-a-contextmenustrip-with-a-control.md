---
title: "Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme"
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a0188a8359b9fd2453b8e38502203c5e04ad4f12
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Nasıl yapılır: ContextMenuStrip'ni Bir Denetimle İlişkilendirme
Kısayol menüleri ve denetimleri oluşturduktan sonra kullanıcı denetimi tıklattığında verilen kısayol menüsünü görüntülemek için aşağıdaki yordamları kullanın. Bu yordamları ilişkilendirmek bir <xref:System.Windows.Forms.ContextMenuStrip> ve bir Windows formu ile bir <xref:System.Windows.Forms.ToolStrip> denetim.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Bir Windows formunda bir ContextMenuStrip ilişkilendirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> ilişkili adı özelliğine <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>ToolStrip denetimi ile bir ContextMenuStrip ilişkilendirmek için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> ilişkili adı özelliğine <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Örnek  
 Windows Form aşağıdaki kod örneği oluşturur ve bir <xref:System.Windows.Forms.ToolStrip>ve farklı bir ilişkilendirir <xref:System.Windows.Forms.ContextMenuStrip> denetimi ile bunların her biri.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Nasıl yapılır: Bir ContextMenuStrip'e Menü Öğeleri Ekleme](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [ContextMenuStrip Denetimi](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
