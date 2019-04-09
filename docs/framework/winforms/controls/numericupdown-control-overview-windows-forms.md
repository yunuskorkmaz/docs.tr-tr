---
title: NumericUpDown Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
ms.openlocfilehash: 218eb685e546acac76a18450612a1601ab87276b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109882"
---
# <a name="numericupdown-control-overview-windows-forms"></a>NumericUpDown Denetimine Genel Bakış (Windows Forms)
<xref:System.Windows.Forms.NumericUpDown> Denetimi bir birleşimini bir metin kutusu ve bir çift değer ayarlamak için kullanıcının tıklayabileceği oklar gibi görünüyor. Denetim, görüntüler ve sabit sayısal değerli Seçenekleri listesinden tek bir sayısal değer ayarlar. Kullanıcı, artırmak ve sayı tıklayarak yukarı ve aşağı ok tuşlarını, yukarı ve aşağı ok tuşlarına basarak ya da denetiminin metin kutusu bölümünde bir sayı yazmak azaltın. Yukarı Ok tuşuna tıklayarak sayısını en doğru taşır; Aşağı Ok tuşuna tıklayarak sayısını en doğru taşır.  
  
 Ses denetimini müzik player uygulaması oluşturmak istiyorsanız çok yönlü işlevselliğini nedeniyle bu belirgin seçim, örneğin, denetimidir. <xref:System.Windows.Forms.NumericUpDown> Denetimi, Windows Denetim Masası'ndaki birçok uygulamada kullanılır.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Denetimin metin kutusunda görüntülenen sayı bir çeşitli biçimlerde dahil olmak üzere, onaltılık olabilir. Daha fazla bilgi için [nasıl yapılır: Windows Forms NumericUpDown denetiminin biçimini ayarlama](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md). Anahtar özellikleri denetimin <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (varsayılan değer 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (varsayılan değer 0), ve <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (varsayılan değer 1). <xref:System.Windows.Forms.NumericUpDown.Value%2A> Özelliği denetim içinde seçilen geçerli numarasını ayarlar. <xref:System.Windows.Forms.NumericUpDown.Increment%2A> Özelliğini ayarlar kaç kullanıcı tıkladığında yukarı veya aşağı ok ayarlanır tutar. Odağı denetimi kapalı taşındığında, herhangi bir türü belirtilmiş giriş karşı minimum ve maksimum sayısal değerler doğrulanır. Denetim numaraları kullanıcı sürekli olarak bastığında yukarı veya aşağı ok, taşıyan hızını artırabilir ile <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> özelliği. Denetimin önemli yöntemlerdir <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown Denetimi](numericupdown-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama](how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
