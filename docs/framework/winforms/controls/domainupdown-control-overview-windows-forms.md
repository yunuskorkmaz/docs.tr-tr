---
title: DomainUpDown Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965308"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimi aslında bir metin kutusu ve bir liste üzerinde yukarı veya aşağı taşımak için bir çift düğme birleşimidir. Denetim, bir seçenek listesinden bir metin dizesi görüntüler ve ayarlar. Kullanıcı, yukarı ve aşağı ok tuşlarına basarak veya listedeki bir öğeyle eşleşen bir dize yazarak bir listede gezinmek için yukarı ve aşağı düğmelere tıklayarak dizeyi seçebilir. Bu denetim için olası bir kullanım, alfabetik olarak sıralanan bir ad listesinden öğe seçmek içindir.  
  
> [!NOTE]
> Listeyi sıralamak için <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğini olarak `true`ayarlayın.  
  
 Bu denetimin işlevi, liste kutusu veya Birleşik giriş kutusuna çok benzer, ancak çok az alan kaplar.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin anahtar özellikleri, <xref:System.Windows.Forms.DomainUpDown.Items%2A> <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>' dir. <xref:System.Windows.Forms.DomainUpDown.Items%2A> Özelliği, metin değerleri denetimde görüntülenen nesnelerin listesini içerir. <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> , Olarak`false`ayarlanırsa, denetim otomatik olarak kullanıcının oluşturduğu metni tamamlar ve listedeki bir değerle eşleştirir. <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> Olarak`true`ayarlanırsa, son öğeyi geçen öğe, sizi listedeki ilk öğeye götürür ve tam tersi olur. Denetimin anahtar yöntemleri ve ' <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>dir.  
  
 Bu denetim yalnızca metin dizelerini görüntüler. Sayısal değerleri görüntüleyen bir denetim istiyorsanız, <xref:System.Windows.Forms.NumericUpDown> denetimi kullanın. Daha fazla bilgi için bkz. [NumericUpDown denetimine genel bakış](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
