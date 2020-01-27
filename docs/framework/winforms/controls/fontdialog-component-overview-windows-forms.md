---
title: FontDialog Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745697"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FontDialog> bileşeni, sistemde yüklü olan yazı tiplerini açığa çıkarmak için kullanılan standart Windows **yazı tipi** iletişim kutusu olan önceden yapılandırılmış bir iletişim kutusudur. Kendi iletişim kutusunu yapılandırmak yerine, yazı tipi seçimi için basit bir çözüm olarak Windows tabanlı uygulamanızın içinde kullanın.  
  
 Varsayılan olarak, iletişim kutusu yazı tipi, yazı tipi stili ve boyut için liste kutularını gösterir; Üstü çizili ve altı çizili gibi efektler için onay kutuları; Betik için bir açılır liste; ve yazı tipinin nasıl görüneceğini gösteren bir örnek. (Komut dosyası, örneğin Ibranice veya Japonca gibi belirli bir yazı tipi için kullanılabilen farklı karakter betikleri anlamına gelir.) Yazı tipi iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi çağırın.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Bileşenin görünümünü yapılandıran bir dizi özelliği vardır. İletişim kutusu seçimlerini ayarlamaya yönelik özellikler <xref:System.Windows.Forms.FontDialog.Font%2A> ve <xref:System.Windows.Forms.FontDialog.Color%2A>. <xref:System.Windows.Forms.FontDialog.Font%2A> özelliği, yazı tipi, stil, boyut, komut dosyası ve etkileri belirler; Örneğin, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog Bileşeni](fontdialog-component-windows-forms.md)
