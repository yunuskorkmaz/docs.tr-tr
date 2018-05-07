---
title: DomainUpDown Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 21d28caf490b008570cbd6280afff3114b0f4bfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimidir aslında bir metin kutusu bileşimini ve listesini yukarı veya aşağı taşıma için düğmeler çifti. Denetim görüntüler ve seçenekler listesinden bir metin dizesini ayarlar. Kullanıcı düğmeleri listesini taşımak için yukarı ve aşağı tıklatarak yukarı ve aşağı ok tuşlarına basarak veya listeden bir öğe eşleşen bir dize yazarak dize seçebilirsiniz. Öğe adları alfabetik olarak sıralanan bir listesinden seçmek için bu denetim için bir olası kullanımı içindir.  
  
> [!NOTE]
>  Sıralamak için ayarlanmış <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğine `true`.  
  
 Bu denetim işlevi liste kutusu veya birleşik giriş kutusu çok benzer, ancak çok az alanı kaplar.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özellikler denetiminin <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Özellik metin değerleri denetiminde görüntülenen nesnelerin listesini içerir. Varsa <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ayarlanır `false`, kullanıcı türleri ve listesindeki bir değeri ile eşleşen metin denetimi otomatik olarak tamamlar. Varsa <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ayarlanır `true`, son öğenin kaydırma yönlendirilirsiniz ilk öğeye listesinde ve tersi. Denetimin anahtar yöntemleri <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> ve <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Bu denetim yalnızca metin dizelerini görüntüler. Sayısal değerler görüntüleyen bir denetim istiyorsanız kullanın <xref:System.Windows.Forms.NumericUpDown> denetim. Daha fazla bilgi için bkz: [NumericUpDown denetimine genel bakış](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DomainUpDown>  
 [DomainUpDown Denetimi](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
