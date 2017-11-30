---
title: "Nasıl Yapılır: Bir Uygulama için ToolStrip Oluşturucusunu Ayarlama"
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
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b717fc5c09d625982a1b573c6c777b7fbdccc2b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>Nasıl Yapılır: Bir Uygulama için ToolStrip Oluşturucusunu Ayarlama
Görünümünü özelleştirebilirsiniz, <xref:System.Windows.Forms.ToolStrip> tek tek denetimleri veya tüm <xref:System.Windows.Forms.ToolStrip> uygulamanızda denetimleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için özel Oluşturucu seçmeli olarak uygulanacak gösterilmiştir bir <xref:System.Windows.Forms.ToolStrip> denetim ve <xref:System.Windows.Forms.MenuStrip> denetim.  
  
 Bu kod örneği kullanmak için derleme ve uygulamayı çalıştırın ve ardından gelen özel Perforator kapsamını seçin <xref:System.Windows.Forms.ComboBox> denetim. Tıklatın **Uygula** Oluşturucu ayarlamak için.  
  
 Özel menü öğesi işleme görmek için seçin <xref:System.Windows.Forms.MenuStrip> gelen seçeneği <xref:System.Windows.Forms.ComboBox> denetlemek, tıklatın **Uygula**ve ardından açın **dosya** menü öğesi.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 Ayarlama <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu tümüne uygulamak için özellik <xref:System.Windows.Forms.ToolStrip> uygulamanızda denetimleri.  
  
 Ayarlama <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> birey için özel Oluşturucu uygulamak için özellik <xref:System.Windows.Forms.ToolStrip> denetim.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Design, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [ToolStrip denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
