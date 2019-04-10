---
title: Windows Formları Tasarımcısında Tasarım Zamanı Hataları
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 7ee4ce1d6efdc4927fc2d20100f0b12f7405261f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213148"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Windows Formları Tasarımcısında Tasarım Zamanı Hataları
Bu konuda, Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesinin kullanımını ve anlamı açıklanmaktadır. Bu hata listesi görüntülenirse, tasarımcıda bir hatayı, ancak kodunuzda hataları düzeltmek için yardımcı olması amacıyla yorumladığınıza değil.  
  
 Bu hata listesi temel bir anlayış hatalar hakkında ayrıntılı bilgi sağlamak ve olası çözümler önerme uygulamalarınızın hatalarını ayıklamanıza yardımcı olur.  
  
## <a name="the-design-time-error-list-interface"></a>Tasarım zamanı hata listesini arabirimi  
 Windows Form Tasarımcısı yüklenemezse, tasarımcıda bir hata listesi görünür. Hataların kategorilere ayrılır. Örneğin, bunlar bildirilmemiş değişkenler dört örneğine sahipseniz, aynı hata kategorisi gruplandırılır. Her hata kategorisi hata özetler kısa bir açıklama içerir.  
  
 Genişletmek veya bir hata kategori hata kategorisi başlığı tıklayarak ya da genişletme/daraltma Köşeli Çift Ayraca tıklayarak Daralt. Hata kategorisi genişlettiğinizde, aşağıdaki ek Yardım görüntülenir:  
  
-   Bu hatanın örnekleri.  
  
-   Bu hatayla ilgili Yardım.  
  
-   Bu hata hakkındaki Forum gönderileri.  
  
### <a name="instances-of-this-error"></a>Bu hatanın örnekleri  
 Ek hata geçerli projenizdeki tüm örneklerini listele Yardım. Birçok hata şu biçimde kesin bir konuma içerir: *[Proje adı]* *[Form adı]* satır:*[satır numarası]* sütun:*[sütun numarası]*. **Koduna Git** bağlantı kodunuzda hatanın oluştuğu konumuna götürür.  
  
 Çağrı yığını şu hata ile ilişkili ise, tıklayabilirsiniz **çağrı yığını Göster** bağlantı, çağrı yığını gösterilecek hata, daha fazla genişletir. Yığın İnceleme hata ayıklama değerli bilgiler sağlayabilir. Örneğin, bir hata oluştu önce çağrılan işlevler izleyebilirsiniz. Çağrı yığınını seçilebilir, böylelikle kopyalayın ve kaydedin.  
  
> [!NOTE]
>  Visual Basic'te, tasarım zamanı hata listesini birden fazla hata görüntülemez ancak birden fazla aynı hata görüntülenebilir. Visual C++'da hataları bağlantıları/satır numarası bağlantıları goto kod yok.  
  
### <a name="help-with-this-error"></a>Bu hatayla ilgili Yardım  
 Hatanın ilişkili bir MSDN Yardım konusu için bir bağlantı içeriyorsa, Ek Yardım Yardım konusunun bağlantısını içerir. Bağlantıya tıkladığında, ilişkili bir Yardım konusu Visual Studio'da görünür.  
  
### <a name="forum-posts-about-this-error"></a>Bu hata hakkındaki Forum gönderileri  
 Ek Yardım MSDN forum gönderilerini hata ile ilgili bir bağlantı içerir. Forumlar, hata iletisi dizesi göre aranır. Ayrıca aşağıdaki forumları aramayı deneyin:  
  
-   [Windows Forms Tasarımcısı Forumu](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms forumları](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Yoksay ve devam et  
 Hata koşulu yoksaymak ve tasarımcı yüklemeye devam etmek seçebilirsiniz. Bu eylem seçme içinde beklenmeyen davranışlara neden olabilir. Örneğin, denetimleri tasarım yüzeyinde görünmeyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Zamanı Geliştirme Sorunlarını Giderme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Denetim ve Bileşen Yazmada Sorun Giderme](troubleshooting-control-and-component-authoring.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Windows Form Tasarımcısı Hata İletileri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
