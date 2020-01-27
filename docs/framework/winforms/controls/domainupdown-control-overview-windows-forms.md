---
title: DomainUpDown Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 86703a96d4845414d043161e0efa67bfde9278db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745853"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimi aslında bir metin kutusu ve bir liste üzerinde yukarı veya aşağı taşımak için bir çift düğme birleşimidir. Denetim, bir seçenek listesinden bir metin dizesi görüntüler ve ayarlar. Kullanıcı, yukarı ve aşağı ok tuşlarına basarak veya listedeki bir öğeyle eşleşen bir dize yazarak bir listede gezinmek için yukarı ve aşağı düğmelere tıklayarak dizeyi seçebilir. Bu denetim için olası bir kullanım, alfabetik olarak sıralanan bir ad listesinden öğe seçmek içindir.  
  
> [!NOTE]
> Listeyi sıralamak için <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğini `true`olarak ayarlayın.  
  
 Bu denetimin işlevi, liste kutusu veya Birleşik giriş kutusuna çok benzer, ancak çok az alan kaplar.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin temel özellikleri <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> özelliği, metin değerleri denetimde görüntülenen nesnelerin listesini içerir. <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> `false`olarak ayarlanırsa, denetim otomatik olarak Kullanıcı tarafından belirlenen metni tamamlar ve listedeki bir değerle eşleştirir. <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> `true`olarak ayarlanırsa, son öğeden geçen kaydırma sizi listedeki ilk öğeye götürür ve bunun tersini alır. Denetimin anahtar yöntemleri <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> ve <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Bu denetim yalnızca metin dizelerini görüntüler. Sayısal değerleri görüntüleyen bir denetim istiyorsanız, <xref:System.Windows.Forms.NumericUpDown> denetimini kullanın. Daha fazla bilgi için bkz. [NumericUpDown denetimine genel bakış](numericupdown-control-overview-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
