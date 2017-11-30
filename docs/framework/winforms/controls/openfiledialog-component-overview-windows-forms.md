---
title: "OpenFileDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35c947e3efbb9b2e5df775f83ffc6068e49c84e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.OpenFileDialog> bir önceden yapılandırılmış iletişim kutusu bir bileşendir. Aynı olduğundan **açık dosya** Windows işletim sistemi tarafından kullanıma sunulan iletişim kutusu. Öğesinden devralınan <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="using-this-component"></a>Bu bileşeni kullanma  
 Bu bileşen, Windows tabanlı bir uygulama içinde kendi iletişim kutusu yapılandırma yerine dosya seçimi için basit bir çözüm kullanın. Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılara hemen alışkın olduğu uygulamalar oluşturun. Ancak, aklınızda bulundurun olduğunda kullanarak <xref:System.Windows.Forms.OpenFileDialog> bileşeni, kendi dosya açılırken mantığı yazma gerekir.  
  
 Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem. Kullanıcılar ile açılması için çoklu seçim dosyalarını etkinleştirebilir <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> özelliği. Ayrıca, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> özelliği salt okunur onay kutusu iletişim kutusunda görünüp görünmeyeceğini belirler. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Özelliği, salt okunur onay kutusunun seçili olup olmadığını belirtir. Son olarak, <xref:System.Windows.Forms.FileDialog.Filter%2A> özelliği ayarlar iletişim kutusundaki "Dosya türü" görünür seçimleri belirleyen geçerli dosya adı filtre dizesi,.  
  
 Bir form için eklendiğinde <xref:System.Windows.Forms.OpenFileDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog bileşeni](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
