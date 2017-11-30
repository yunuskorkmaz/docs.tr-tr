---
title: "NumericUpDown Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1afb128fd5e098a59fa2636f09998a2a463c926
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown Denetimine Genel Bakış (Windows Forms)
<xref:System.Windows.Forms.NumericUpDown> Denetimi kullanıcının bir değer ayarlamak için tıklatabileceği okları çifti ve bir metin kutusu birleşimini gibi görünüyor. Denetim görüntüler ve sabit sayısal değer seçenekler listesinden tek bir sayısal değer ayarlar. Kullanıcı artırmak ve kaç yukarı tıklayarak ve oklar, aşağı yukarı ve aşağı ok tuşlarına basarak veya bir sayı denetim metin kutusu parçası yazarak azaltın. Yukarı Ok tuşuna tıklayarak sayı en doğru taşır; AŞAĞI ok tuşunu tıklatıldığında, en düşük doğru numarası taşınır.  
  
 Müzik çalar uygulaması için bir birim denetim oluşturmak istiyorsanız, çok yönlü işlevselliğini nedeniyle bu denetim bir belirgin, örneğin, seçimdir. <xref:System.Windows.Forms.NumericUpDown> Denetimi birçok Windows Denetim Masası uygulamalarda kullanılır.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Denetimin metin kutusunda görüntülenen numaralarının bir çeşitli biçimlerde dahil olmak üzere, onaltılık olabilir. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms NumericUpDown denetiminin biçimini ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Anahtar özellikler denetiminin <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (varsayılan değer 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (varsayılan değer 0), ve <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (varsayılan değer 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Özelliği denetim içinde seçilen geçerli numarasını ayarlar. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Özelliği ayarlar numarası kullanıcı tıkladığında bir yukarı veya aşağı ok ayarlanır tutar. Odağı denetimi devre dışı geçtiğinde, herhangi bir yazılı giriş karşı ve en düşük sayısal değerleri doğrulanacak. Kullanıcı sürekli açık bastığında veya aşağı ok, numaraları denetimi taşır hızını artırabilir ile <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> özelliği. Denetimin anahtar yöntemleri <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown denetimi](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms NumericUpDown denetiminin biçimini ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [TextBox denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
