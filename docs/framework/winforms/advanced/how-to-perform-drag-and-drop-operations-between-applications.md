---
title: "Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 513c6b2a15502625e4b42aeee4947ff36e4bfd17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme
Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme Bu eylem, uygulama içinde etkinleştirme daha farklı "arasında kurulan Sözleşmesi" göre katılan her iki uygulamayı davranır sürece <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> ve <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Özellikler.  
  
 Aşağıdaki yordamda, oluşturduğunuz Windows tabanlı bir uygulama ve uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek için Windows işletim sistemiyle eklenmiştir WordPad sözcük işlemci kullanır. WordPad sürüklenip bırakılmasına metnin için izin verilen etkileri belirli kümesine sahiptir; Windows tabanlı bir uygulama için kod yazacaksınız bu efektleri ile çalışır. böylece sürükle ve bırak işlemleri başarıyla tamamlandı.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Uygulamalar arasında sürükle ve bırak yordamı gerçekleştirmek için  
  
1.  Yeni bir Windows Forms uygulaması oluşturma.  
  
2.  Ekleme bir <xref:System.Windows.Forms.TextBox> Formunuza denetim.  
  
3.  Yapılandırma <xref:System.Windows.Forms.TextBox> bırakılan veri almak için denetim.  
  
     Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Windows tabanlı uygulamanızı çalıştırın ve uygulama çalışırken, WordPad çalıştırın.  
  
     WordPad sürükle ve bırak işlemleri sağlayan Windows tarafından yüklenen bir metin Düzenleyicisi ' dir. Tuşlarına basarak erişilebilir durumda **Başlat** düğmesi, seçme **çalıştırmak**, yazarak `WordPad` metin kutusuna **çalıştırmak** iletişim kutusu ve tıklayarak**Tamam**.  
  
5.  WordPad açıldıktan sonra bir metin dizesinin içine yazın.  
  
6.  Fare kullanarak, metni seçin ve ardından seçili metnin üzerine sürükleyin <xref:System.Windows.Forms.TextBox> Windows tabanlı uygulamanızda denetim.  
  
     Üzerinden fare olduğunda, gözlemlemek <xref:System.Windows.Forms.TextBox> denetimi (ve sonuç olarak, Yükselt <xref:System.Windows.Forms.Control.DragEnter> olay), imleç ve seçili metne düşürebilir <xref:System.Windows.Forms.TextBox> denetim.  
  
     Ayrıca, yapılandırın, <xref:System.Windows.Forms.TextBox> sürüklenen ve WordPad bırakılan metin dizelerini izin vermek için denetim. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: panoya veri ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Nasıl yapılır: panodan veri alma](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Sürükle ve bırak işlemleri ve Pano desteği](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
