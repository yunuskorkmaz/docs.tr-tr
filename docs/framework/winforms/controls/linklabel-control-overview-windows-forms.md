---
title: LinkLabel Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745218"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimi, Windows Forms uygulamalara Web stili bağlantılar eklemenize olanak tanır. <xref:System.Windows.Forms.Label> denetimini kullanabileceğiniz her şey için <xref:System.Windows.Forms.LinkLabel> denetimini kullanabilirsiniz; Ayrıca, metnin bir bölümünü bir dosya, klasör veya Web sayfasına bağlantı olarak da ayarlayabilirsiniz.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>LinkLabel denetimiyle yapabilecekleriniz  
 <xref:System.Windows.Forms.Label> denetiminin tüm özelliklerine, yöntemlerine ve olaylarına ek olarak, <xref:System.Windows.Forms.LinkLabel> denetimi köprüler ve bağlantı renkleri için özelliklere sahiptir. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliği, bağlantıyı etkinleştiren metnin alanını ayarlar. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>ve <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> özellikleri bağlantının renklerini ayarlar. <xref:System.Windows.Forms.LinkLabel.LinkClicked> olayı, bağlantı metni seçildiğinde ne olacağını belirler.  
  
 <xref:System.Windows.Forms.LinkLabel> denetiminin en basit kullanımı, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliğini kullanarak tek bir bağlantı görüntülemektir, ancak <xref:System.Windows.Forms.LinkLabel.Links%2A> özelliğini kullanarak birden çok köprü da görüntüleyebilirsiniz. <xref:System.Windows.Forms.LinkLabel.Links%2A> özelliği bir bağlantı koleksiyonuna erişmenizi sağlar. Ayrıca, her bir <xref:System.Windows.Forms.LinkLabel.Link> nesnesinin <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> özelliğindeki verileri de belirtebilirsiniz. <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> özelliğinin değeri, görüntülenecek dosyanın konumunu veya bir Web sitesinin adresini depolamak için kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.LinkLabel>
- [Etiket Denetimine Genel Bakış](label-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
