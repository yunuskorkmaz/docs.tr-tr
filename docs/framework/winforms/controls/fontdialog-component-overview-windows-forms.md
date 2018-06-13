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
ms.openlocfilehash: 3a4707ffe471161988d0526ce0908b37299f3e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526884"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.FontDialog> bileşenidir standart Windows bir önceden yapılandırılmış iletişim kutusu **yazı tipi** sistemde yüklü yazı tiplerini kullanıma sunmak için kullanılan iletişim kutusu. Basit bir çözüm olarak, Windows tabanlı uygulamanızda kendi iletişim kutusu yapılandırma yerine yazı tipi seçimi için kullanın.  
  
 Varsayılan olarak, liste kutuları iletişim kutusu, yazı tipini gösterir. yazı tipi stili ve boyutu; üstü çizili ve alt çizgi gibi etkileri onay kutularını; komut dosyası için aşağı açılan listesi; ve yazı tipi nasıl görüneceğini bir örnek. (Betik verilen yazı tipi için kullanılabilen farklı karakter betikleri Örneğin, İbranice veya Japonca ifade eder.) Yazı tipi iletişim kutusu görüntülemek için arama <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Bileşen bir dizi görünümünü yapılandırma özellikleri vardır. İletişim kutusu seçimleri ayarlamak Özellikler <xref:System.Windows.Forms.FontDialog.Font%2A> ve <xref:System.Windows.Forms.FontDialog.Color%2A>. <xref:System.Windows.Forms.FontDialog.Font%2A> Özelliği ayarlar yazı tipini, stili, boyutu, komut dosyası ve etkiler; Örneğin, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FontDialog>  
 [FontDialog Bileşeni](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
