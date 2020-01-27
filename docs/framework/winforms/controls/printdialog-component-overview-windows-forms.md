---
title: PrintDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728671"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog Bileşenine Genel Bakış (Windows Forms)

Windows Forms [PrintDialog](printdialog-component-windows-forms.md) bileşeni, bir yazıcı seçmek, yazdırılacak sayfaları seçmek ve Windows tabanlı uygulamalarda yazdırma ile ilgili diğer ayarları belirlemek için kullanılan önceden yapılandırılmış bir iletişim kutusudur. Kendi iletişim kutusunu yapılandırmak yerine yazıcı ve yazdırma ile ilgili ayarlar için basit bir çözüm olarak kullanın. Kullanıcıların belgelerinin birçok bölümünü yazdırmasını sağlayabilirsiniz: tümünü yazdır, seçili sayfa aralığını Yazdır veya bir seçimi yazdır. Standart Windows iletişim kutularına bağlı olarak, temel işlevselliği kullanıcılara hemen tanıdık olan uygulamalar oluşturursunuz. <xref:System.Windows.Forms.PrintDialog> bileşen <xref:System.Windows.Forms.CommonDialog> sınıfından devralır.

## <a name="working-with-the-component"></a>Bileşenle çalışma

Çalışma zamanında iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın. Bu bileşen, tek bir yazdırma işiyle (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya tek bir yazıcının (<xref:System.Drawing.Printing.PrinterSettings> sınıfının) ayarlarıyla ilgili özelliklere sahiptir. Bunlardan biri sırasıyla birden çok yazıcı tarafından paylaşılabilir.

Bir forma eklendiğinde <xref:System.Windows.Forms.PrintDialog> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog Bileşeni](printdialog-component-windows-forms.md)
