---
title: DomainUpDown Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 851c02747a2414e34a5e9d35bdc7d1df916efce0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718902"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimidir aslında bir birleşimini bir metin kutusu ve bir çift bir listede yukarı veya aşağı taşımak için düğmeler. Denetim, görüntüler ve seçenekler listesinden bir metin dizesini ayarlar. Kullanıcı, bir listesi geçmek düğmelerini yukarı ve aşağı tıklayarak yukarı ve aşağı ok tuşlarına basarak veya bir öğe listesinde eşleşen bir dize yazarak dize seçebilirsiniz. Bir olası bu denetim için öğe adları alfabetik olarak sıralanmış bir listesinden seçmek için kullanılır.  
  
> [!NOTE]
>  Listeyi sıralamak için ayarlanmış <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğini `true`.  
  
 Bu denetimin işlev birleşik giriş kutusu ve liste kutusu için çok benzer, ancak çok az alanı kaplar.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özellikleri denetimin <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Özelliği, metin değerleri denetimde görüntülenen nesnelerin listesini içerir. Varsa <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ayarlanır `false`, denetimin kullanıcı türleri ve listedeki bir değeri ile eşleşen metni otomatik olarak tamamlar. Varsa <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ayarlanır `true`, son öğenin kaydırma yönlendirilirsiniz ilk öğeye listesinde ve bunun tersi de geçerlidir. Denetimin önemli yöntemlerdir <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> ve <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Bu denetim yalnızca metin dizelerini görüntüler. Sayısal değerleri görüntüleyen bir denetimi istiyorsanız kullanın <xref:System.Windows.Forms.NumericUpDown> denetimi. Daha fazla bilgi için [NumericUpDown denetimine genel bakış](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
