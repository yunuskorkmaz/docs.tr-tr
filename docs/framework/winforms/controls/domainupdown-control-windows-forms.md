---
title: DomainUpDown Denetimi
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745831"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown Denetimi (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimi bir metin kutusu ve bir liste üzerinde yukarı veya aşağı taşımak için bir çift düğme gibi görünür. Denetim, bir seçenek listesinden bir metin dizesi görüntüler ve ayarlar. Kullanıcı, yukarı ve aşağı ok tuşlarına basarak veya listedeki bir öğeyle eşleşen bir dize yazarak bir listede gezinmek için yukarı ve aşağı düğmelere tıklayarak dizeyi seçebilir. Bu denetim için olası bir kullanım, alfabetik olarak sıralanan bir ad listesinden öğe seçmek içindir. (Listeyi sıralamak için <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğini `true`olarak ayarlayın.) Bu denetimin işlevi, liste kutusu veya Birleşik giriş kutusuna çok benzer, ancak çok az alan kaplar.  
  
 Denetimin temel özellikleri <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>. <xref:System.Windows.Forms.DomainUpDown.Items%2A> özelliği, metin değerleri denetimde görüntülenen nesnelerin listesini içerir. <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> `false`olarak ayarlanırsa, denetim otomatik olarak Kullanıcı tarafından belirlenen metni tamamlar ve listedeki bir değerle eşleştirir. <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> `true`olarak ayarlanırsa, son öğeden geçen kaydırma sizi listedeki ilk öğeye götürür ve bunun tersini alır. Denetimin anahtar yöntemleri <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> ve <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.  
  
 Bu denetim yalnızca metin dizelerini görüntüler. Sayısal değerleri görüntüleyen bir denetim istiyorsanız, <xref:System.Windows.Forms.NumericUpDown> denetimini kullanın. Daha fazla bilgi için bkz. [NumericUpDown denetimi](numericupdown-control-windows-forms.md) .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DomainUpDown Denetimine Genel Bakış](domainupdown-control-overview-windows-forms.md)  
 <xref:System.Windows.Forms.DomainUpDown> denetiminin genel kavramlarını tanıtır, bu, kullanıcıların metin dizeleri listesinden göz atmasına ve seçim yapmasına olanak tanır.  
  
 [Nasıl yapılır: Windows Forms DomainUpDown Denetimlerine Programlı Olarak Öğe Ekleme](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <xref:System.Windows.Forms.DomainUpDown> denetiminin görüntülemesi gereken metin dizelerinin nasıl belirtileceğini açıklar.  
  
 [Nasıl yapılır: Windows Forms DomainUpDown Denetimlerinden Öğeleri Kaldırma](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 Koddaki <xref:System.Windows.Forms.DomainUpDown> denetiminden öğelerin nasıl silineceğini açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.DomainUpDown>  
 Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Windows Forms Için kullanabileceğiniz denetimler](controls-to-use-on-windows-forms.md)  
 Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.
