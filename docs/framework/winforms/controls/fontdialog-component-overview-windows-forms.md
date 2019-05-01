---
title: FontDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 7f140807bf4b42e530302190042e729c59248e7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789317"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FontDialog> bileşendir standart Windows olan bir önceden yapılandırılmış bir iletişim kutusu **yazı tipi** sistemde yüklü yazı tiplerini kullanıma sunmak için kullanılan iletişim kutusu. Basit bir çözüm olarak, Windows tabanlı uygulama içindeki yazı tipi seçimi yerine kendi iletişim kutusu yapılandırmak için kullanın.  
  
 Varsayılan olarak, liste kutuları iletişim kutusu, yazı tipi için gösterir. yazı tipi stili ve boyutu; üstü çizili ve alt çizgi gibi etkileri için onay kutularını; komut dosyası için bir açılan liste; ve yazı tipi nasıl görüneceğini gösteren bir örnek. (Betik belirli bir yazı tipi için kullanılabilen farklı karakter betikleri gibi İbranice veya Japonca ifade eder.) Yazı tipi iletişim kutusu görüntülemek için çağrı <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Bileşen bir dizi görünümünü Yapılandırma özelliği vardır. İletişim kutusu seçimleri ayarlama özellikleri <xref:System.Windows.Forms.FontDialog.Font%2A> ve <xref:System.Windows.Forms.FontDialog.Color%2A>. <xref:System.Windows.Forms.FontDialog.Font%2A> Özelliğini ayarlar yazı tipini, stili, boyutunu, betik ve etkiler; Örneğin, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog Bileşeni](fontdialog-component-windows-forms.md)
