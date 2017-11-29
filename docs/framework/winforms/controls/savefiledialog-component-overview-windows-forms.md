---
title: "SaveFileDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cbdc1cb96234e302458cbeac6d6ae26b63c956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.SaveFileDialog> bir önceden yapılandırılmış iletişim kutusu bir bileşendir. Standart olarak aynı olduğundan **dosyayı Kaydet** Windows tarafından kullanılan iletişim kutusu. Öğesinden devralınan <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="working-with-the-savefiledialog-component"></a>SaveFileDialog bileşeni ile çalışma  
 Basit bir çözüm kendi iletişim kutusu yapılandırma yerine dosyaları kaydetmek kullanıcıların etkinleştirmek için kullanın. Standart Windows iletişim kutularında bağlı olan temel oluşturduğunuz uygulamaların kullanıcılarına hemen tanıdık bir işlevdir. Ancak, aklınızda bulundurun olduğunda kullanarak <xref:System.Windows.Forms.SaveFileDialog> bileşeni, kendi dosya kaydetme mantığı yazma gerekir.  
  
 Kullanabileceğiniz <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem. Okuma/yazma modu kullanarak bir dosyayı açabilmek için <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi.  
  
 Bir form için eklendiğinde <xref:System.Windows.Forms.SaveFileDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog bileşeni](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
