---
title: NotifyIcon Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742131"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon Bileşenine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşeni genellikle arka planda çalışan işlemlere yönelik simgeler görüntülemek için kullanılır ve zaman içinde bir kullanıcı arabirimi göstermez. Görev çubuğunun durum bildirimi alanındaki bir simgeye tıklanarak erişilebilen bir virüsten koruma programı örnek olarak yer alabilir.

## <a name="key-properties-of-notifyicons"></a>Notifysimgelerinden önemli özellikler

Her <xref:System.Windows.Forms.NotifyIcon> bileşeni durum alanında tek bir simge görüntüler. Üç arka plan işlemleriniz varsa ve her biri için bir simge göstermek istiyorsanız, forma üç <xref:System.Windows.Forms.NotifyIcon> bileşeni eklemeniz gerekir. <xref:System.Windows.Forms.NotifyIcon> bileşenin temel özellikleri <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği, durum alanında görüntülenen simgeyi ayarlar. Simgenin görünmesi için <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin `true`olarak ayarlanması gerekir.

## <a name="notifyicons-options"></a>Notifysimgeler seçenekleri

Kullanıcıya yardımcı olması için balon ipuçlarını, kısayol menülerini ve araç Ipuçlarını bir <xref:System.Windows.Forms.NotifyIcon> ilişkilendirebilirsiniz.

Balon ipucunun görüntülenmesini istediğiniz zaman aralığını belirten <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> yöntemini çağırarak bir <xref:System.Windows.Forms.NotifyIcon> balon ipuçlarını görüntüleyebilirsiniz. Balon ipucunun metin, simge ve başlığını sırasıyla <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> ve <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>ile de belirtebilirsiniz. <xref:System.Windows.Forms.NotifyIcon> bileşenlerinde ayrıca ilişkili araç Ipuçları ve kısayol menüleri bulunabilir. Daha fazla bilgi için bkz. [araç Ipucu bileşenine genel bakış](tooltip-component-overview-windows-forms.md) ve [ContextMenu bileşenine genel bakış](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon Bileşeni](notifyicon-component-windows-forms.md)
