---
title: "Klavye Olaylarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- KeyPress event [Windows Forms]
- keyboards [Windows Forms], keyboard events
- KeyUp event
- KeyDown event
- keyboard events
- events [Windows Forms], keyboard
ms.assetid: d3f3e14b-a459-4ee6-9875-8957e34f8ee9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394ebc503338ad73001aa9859e0aa0d9c3fa42b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-keyboard-events"></a>Klavye Olaylarını Kullanma
Windows Forms programlarının çoğu klavye girişi klavye olayları işleme göre işler. Bu konu, her olay ve sağlanan verileri her olay için kullanmak ne zaman ayrıntılar dahil olmak üzere klavye olayları genel bir bakış sağlar.  Ayrıca bkz. [olay işleyicilerine genel bakış (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [olaylara genel bakış (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\)).  
  
## <a name="keyboard-events"></a>Klavye olayları  
 Windows Forms kullanıcı klavye tuşuna bastığında oluşan iki olayları ve bir kullanıcı bir klavye tuşu bıraktığında bir olay sağlar:  
  
-   <xref:System.Windows.Forms.Control.KeyDown> Olay oluştuktan sonra  
  
-   <xref:System.Windows.Forms.Control.KeyPress> Birden çok kez ne zaman bir kullanıcı aynı tuşunu tutan oluşabilir olay.  
  
-   <xref:System.Windows.Forms.Control.KeyUp> Olayı, bir kullanıcı bir anahtar zaman serbest sonra oluşur.  
  
 Bir kullanıcı bir tuşuna bastığında klavye iletiyi karakter anahtar ya da fiziksel bir anahtar belirtir yükseltmek için hangi olay tabanlı Windows Forms belirler. Karakter ve fiziksel anahtarlar hakkında daha fazla bilgi için bkz: [nasıl klavye girişi çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
 Aşağıdaki tabloda, üç klavye olaylarını açıklar.  
  
|Klavye olayı|Açıklama|Sonuçları|  
|--------------------|-----------------|-------------|  
|<xref:System.Windows.Forms.Control.KeyDown>|Bir kullanıcı bir fiziksel tuşuna bastığında bu olay tetiklenir.|İşleyicisi <xref:System.Windows.Forms.Control.KeyDown> alır:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> sağlayan parametresi <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (fiziksel klavye düğmesi belirtir) özelliği.</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Özelliği (SHIFT, CTRL ya da ALT).</li><li><xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> (Anahtar kodu ve değiştirici birleştirir) özelliği. <xref:System.Windows.Forms.KeyEventArgs> Parametresi de sağlar:<br /><br /> <ul><li><xref:System.Windows.Forms.KeyEventArgs.Handled%2A> Temel denetim anahtar almasını önlemek için ayarlanabilir özelliği.</li><li><xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> Gizlemek için kullanılan özellik <xref:System.Windows.Forms.Control.KeyPress> ve <xref:System.Windows.Forms.Control.KeyUp> bu tuş vuruşu olayları.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyPress>|Anahtarı veya anahtarları sonuç bir karakter tuşuna bastığınızda, bu olay tetiklenir. Örneğin, bir kullanıcı kaydırma ve küçük harf bir büyük harf "A" karakter neden "a" tuşuna bastığında.|<xref:System.Windows.Forms.Control.KeyPress>sonra tetiklenir <xref:System.Windows.Forms.Control.KeyDown>.<br /><br /> <ul><li>İşleyicisi <xref:System.Windows.Forms.Control.KeyPress> alır:</li><li>A <xref:System.Windows.Forms.KeyPressEventArgs> basıldı anahtar karakter kodunu içerir parametresi. Bu karakter kodu her bir karakteri anahtarı ve değiştirici tuşa birleşimi için benzersizdir.<br /><br />     Örneğin, "A" anahtar üretir:<br /><br /> <ul><li>SHIFT tuşuyla basıldıysa 65 karakter kodu</li><li>Veya tek başına basıldığında varsa 97 CAPS LOCK tuşunun,</li><li>Ve 1 ile CTRL tuşunu basılı olduğunda.</li></ul></li></ul>|  
|<xref:System.Windows.Forms.Control.KeyUp>|Bir kullanıcı bir fiziksel anahtar yayımlandığında bu olay tetiklenir.|İşleyicisi <xref:System.Windows.Forms.Control.KeyUp> alır:<br /><br /> <ul><li>A <xref:System.Windows.Forms.KeyEventArgs> parametre:<br /><br /> <ul><li>Sağlayan <xref:System.Windows.Forms.KeyEventArgs.KeyCode%2A> (fiziksel klavye düğmesi belirtir) özelliği.</li><li><xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> Özelliği (SHIFT, CTRL ya da ALT).</li><li><xref:System.Globalization.SortKey.KeyData%2A> (Anahtar kodu ve değiştirici birleştirir) özelliği.</li></ul></li></ul>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Klavye Girdisi](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Klavye Girdisi Nasıl Çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
