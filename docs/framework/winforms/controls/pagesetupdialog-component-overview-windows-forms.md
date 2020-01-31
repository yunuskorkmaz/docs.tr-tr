---
title: PageSetupDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744334"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog Bileşenine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.PageSetupDialog> bileşeni, Windows tabanlı uygulamalarda yazdırma için sayfa ayrıntılarını ayarlamak üzere kullanılan önceden yapılandırılmış bir iletişim kutusudur. Kullanıcıların kendi iletişim kutusunu yapılandırmak yerine sayfa tercihleri ayarlamak için Windows tabanlı uygulamanızda bu uygulamayı basit bir çözüm olarak kullanın. Kullanıcıların kenarlık ve kenar boşluğu ayarlamalarını, üst bilgileri ve altbilgileri ve dikey ya da yatay yönlendirmeyi ayarlamasını sağlayabilirsiniz. Standart Windows iletişim kutularına bağlı olarak, temel işlevselliği kullanıcılara hemen tanıdık olan uygulamalar oluşturursunuz.

## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri

Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın. Bu bileşen, tek bir sayfa (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya herhangi bir belge (<xref:System.Drawing.Printing.PageSettings> sınıfı) ile ilgili olarak ayarlayabileceğiniz özelliklere sahiptir. Ayrıca, <xref:System.Windows.Forms.PageSetupDialog> bileşeni, <xref:System.Drawing.Printing.PrinterSettings> sınıfında depolanan belirli yazıcı ayarlarını belirlemede kullanılabilir.

Bir forma eklendiğinde <xref:System.Windows.Forms.PageSetupDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PageSetupDialog>
- [PageSetupDialog bileşeni](pagesetupdialog-component-windows-forms.md)
