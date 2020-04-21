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
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739511"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.LinkLabel> denetimi, Windows Forms uygulamalarına Web tarzı bağlantılar eklemenize olanak tanır. Denetimi kullanabileceğiniz <xref:System.Windows.Forms.LinkLabel> her şey için <xref:System.Windows.Forms.Label> denetimi kullanabilirsiniz; metnin bir kısmını bir dosya, klasör veya Web sayfasına bağlantı olarak da ayarlayabilirsiniz.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>LinkLabel Denetimi ile Yapabilecekler  
 <xref:System.Windows.Forms.Label> Denetimin tüm özelliklerine, yöntemlerine ve olaylarına <xref:System.Windows.Forms.LinkLabel> ek olarak, denetimin köprüler ve bağlantı renkleri için özellikleri vardır. Özellik, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> bağlantıyı etkinleştiren metnin alanını ayarlar. , <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>ve <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> özellikleri bağlantının renklerini ayarlar. Olay, <xref:System.Windows.Forms.LinkLabel.LinkClicked> bağlantı metni seçildiğinde ne olacağını belirler.  
  
 Denetimin <xref:System.Windows.Forms.LinkLabel> en basit kullanımı <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> özelliği kullanarak tek bir bağlantı görüntülemektir, ancak <xref:System.Windows.Forms.LinkLabel.Links%2A> özelliği kullanarak birden çok köprü de görüntüleyebilirsiniz. Özellik, <xref:System.Windows.Forms.LinkLabel.Links%2A> bir bağlantı koleksiyonuna erişmenizi sağlar. Ayrıca, her bir <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> <xref:System.Windows.Forms.LinkLabel.Link> nesnenin özelliğinde veri belirtebilirsiniz. <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> Özelliğin değeri, görüntülenecek dosyanın konumunu veya Web sitesinin adresini depolamak için kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.LinkLabel>
- [Etiket Denetimine Genel Bakış](label-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms LinkLabel Denetimi ile Bir Nesneye veya Web Sayfasına Bağlama](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Nasıl yapılır: Windows Forms LinkLabel Denetiminin Görünüşünü Değiştirme](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
