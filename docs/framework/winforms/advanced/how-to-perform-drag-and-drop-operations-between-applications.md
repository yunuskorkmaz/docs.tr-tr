---
title: 'Nasıl yapılır: Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 1e9556a69f3f5da4a47c5f5b1a6043a9a73dd8ff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713448"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Nasıl yapılır: Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme
Uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirme Bu eylem, uygulamadaki etkinleştirme değerinden farklı katılan her iki uygulama arasında kurulan "Sözleşme" göre davranır sürece <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> ve <xref:System.Windows.Forms.DragEventArgs.Effect%2A> özellikleri.  
  
 Aşağıdaki yordamda, oluşturduğunuz ve Windows tabanlı bir uygulama ve uygulamalar arasında sürükle ve bırak işlemleri gerçekleştirmek için Windows işletim sistemi ile birlikte sağlanan WordPad sözcük işlemci kullanır. WordPad belirli bir dizi olan metin için izin verilen efektleri sürüklenebilen ve bırakılan vardır; Sürükle ve bırak işlemleri başarıyla tamamlandı, Windows tabanlı bir uygulama için kod yazacaksınız bu efektleri ile çalışır.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Uygulamalar arasında sürükle ve bırak yordam gerçekleştirmek için  
  
1.  Yeni bir Windows Forms uygulaması oluşturun.  
  
2.  Ekleme bir <xref:System.Windows.Forms.TextBox> form denetimi.  
  
3.  Yapılandırma <xref:System.Windows.Forms.TextBox> bırakılan veri almasına izin denetimi.  
  
     Daha fazla bilgi için [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Windows tabanlı uygulamanızı çalıştırın ve uygulama çalışırken WordPad çalıştırın.  
  
     WordPad sürükle ve bırak işlemleri sağlayan Windows tarafından yüklenen bir metin düzenleyicidir. Tuşuna basarak erişilebilir durumda **Başlat** düğmesi, seçme **çalıştırmak**, ardından yazarak `WordPad` metin kutusuna **çalıştırmak** iletişim kutusu ve tıklayarak**Tamam**.  
  
5.  WordPad açıldıktan sonra içine bir metin dizesi yazın.  
  
6.  Fareyi kullanarak, metni seçin ve ardından seçili metin üzerine sürükleyin <xref:System.Windows.Forms.TextBox> Windows tabanlı uygulama denetimi.  
  
     Üzerine fare imlecinizle mesajının görüntülendiğini görün <xref:System.Windows.Forms.TextBox> denetimi (ve sonuç olarak, yükseltme <xref:System.Windows.Forms.Control.DragEnter> olay), imleç ve seçilen metne bırakabilirsiniz <xref:System.Windows.Forms.TextBox> denetimi.  
  
     Buna ek olarak, yapılandırabileceğiniz, <xref:System.Windows.Forms.TextBox> sürüklenebilen ve WordPad bırakılan metin dizelerini izin vermek için denetim. Daha fazla bilgi için [izlenecek yol: Windows Forms'ta sürükle ve bırak işlemi gerçekleştirme](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Panoya veri ekleme](how-to-add-data-to-the-clipboard.md)
- [Nasıl yapılır: Panodan veri alma](how-to-retrieve-data-from-the-clipboard.md)
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
