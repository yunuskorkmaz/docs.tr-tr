---
title: PrintDialog bileşenini görüntüleme
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285161"
---
# <a name="how-to-display-the-printdialog-component"></a>PrintDialog bileşenini görüntüleme

<xref:System.Windows.Forms.PrintDialog> Kullanıcılarınızın birçoğu ile tanıdık gelecektir standart Windows yazdırma iletişim kutusunda bir bileşendir. Kullanıcılarınızın rahat hemen olacağından, kullanabilmeniz için faydalı olacaktır <xref:System.Windows.Forms.PrintDialog> bileşeni.

## <a name="to-display-the-printdialog-component"></a>PrintDialog bileşenini görüntüleme için

- Çağrı <xref:System.Windows.Forms.Form.ShowDialog%2A> uygulamanızın kodundaki yöntemi.

     Bileşen gösterilen sonra kullanıcılar, yazdırma işinin özelliklerini ayarlama etkileşim. Bunlar kaydedilir <xref:System.Drawing.Printing.PrinterSettings> sınıfı (ve <xref:System.Drawing.Printing.PageSettings> kullanıcı erişirse, sınıf [PageSetupDialog bileşeni](pagesetupdialog-component-windows-forms.md) aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni), yazdırma işi ile ilişkili. Daha sonra yazdırma işinin özelliklerini belirlemek için ayarladıkları çağrıları özelliklerine de yapabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [PrintPreviewDialog Denetimi](printpreviewdialog-control-windows-forms.md)
- [PrintDialog Bileşeni](printdialog-component-windows-forms.md)
- [Windows Forms Yazdırma Desteği](../advanced/windows-forms-print-support.md)
- [Windows Forms Denetimleri](index.md)