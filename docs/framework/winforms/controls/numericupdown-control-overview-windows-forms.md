---
title: NumericUpDown Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 3e24fa543df9028e9866d91ec60c3cf88578ac56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740806"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown Denetimine Genel Bakış (Windows Forms)
<xref:System.Windows.Forms.NumericUpDown> denetim, bir metin kutusu ve kullanıcının bir değeri ayarlamak için tıklabileceği bir çift ok gibi görünür. Denetim, sabit sayısal değer seçimlerinin bir listesinden tek bir sayısal değer görüntüler ve ayarlar. Kullanıcı yukarı ve aşağı ok tuşlarına basarak veya denetimin metin kutusu kısmına bir sayı yazarak yukarı ve aşağı okları tıklatarak sayıyı artırabilir ve azaltabilir. YUKARı ok tuşuna tıklamak sayıyı en yüksek değere doğru hareket ettirir; AŞAĞı ok tuşuna tıklamak sayıyı en düşük değere doğru hareket ettirir.  
  
 Bu denetim, çok yönlü işlevselliği nedeniyle, örneğin, bir müzik oynatıcı uygulaması için bir birim denetimi oluşturmak istiyorsanız, belirgin bir seçenektir. <xref:System.Windows.Forms.NumericUpDown> denetimi birçok Windows Denetim Masası uygulamasında kullanılır.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Denetimin metin kutusunda görünen sayılar onaltılık dahil olmak üzere çeşitli biçimlerde olabilir. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms NumericUpDown denetimi Için biçim ayarlama](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Denetimin temel özellikleri <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (varsayılan değer 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (varsayılan değer 0) ve <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (varsayılan değer 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği, denetimde seçilen geçerli sayıyı ayarlar. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> özelliği, Kullanıcı yukarı veya aşağı oka tıkladığında, sayının ayarlandığı miktarı ayarlar. Odak denetimin dışına taşınırsa, yazılan herhangi bir giriş en düşük ve en büyük sayısal değerlere göre doğrulanacak. Kullanıcı yukarı veya aşağı oka <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> özelliği ile sürekli olarak bastığında denetimin sayılar üzerinden geçme hızını artırabilirsiniz. Denetimin anahtar yöntemleri <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown Denetimi](numericupdown-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
