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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015966"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Windows Form Tasarımcısı tasarım zamanı hataları

Bu konuda, Windows Form Tasarımcısı yükleyemediğinde Visual Studio 'da görünen tasarım zamanı hata listesinin anlamı ve kullanımı açıklanmaktadır. Bu hata listesi görünürse, bu hatayı tasarımcıda hata olarak yorumlayamazsınız, ancak kodunuzdaki hataları düzeltmeye yardımcı olur.

Bu hata listesini temel olarak anlamak, hatalar hakkında ayrıntılı bilgi sağlayarak ve olası çözümleri önererek uygulamalarınızın hatalarını ayıklamanıza yardımcı olur.

## <a name="the-design-time-error-list-interface"></a>Tasarım zamanı hata listesi arabirimi

Windows Form Tasarımcısı yüklenamazsa, tasarımcıda bir hata listesi görüntülenir. Hatalar kategoriler halinde gruplandırılır. Örneğin, bildirilmemiş değişkenlerin dört örneği varsa, bunlar aynı hata kategorisi içinde gruplandırılır. Her hata kategorisi, hatayı özetleyen kısa bir açıklama içerir.

Hata kategorisi başlığına tıklayarak ya da Genişlet/Daralt köşeli çift ayraca tıklayarak bir hata kategorisini genişletebilir veya daraltabilirsiniz. Bir hata kategorisini genişlettiğinizde, aşağıdaki ek yardım görüntülenir:

- Bu hatanın örnekleri.

- Bu hatayla ilgili yardım.

- Bu hatayla ilgili forum gönderileri.

### <a name="instances-of-this-error"></a>Bu hatanın örnekleri

Ek Yardım, geçerli projenizde hatanın tüm örneklerini listeler. Birçok hata, Şu biçimdeki kesin bir konum içerir: *[proje adı]* *[Form adı]* satır: *[satır numarası]* sütun: *[sütun numarası]* . **Koda git** bağlantısı sizi kodunuzda Hatanın gerçekleştiği konuma götürür.

Bir çağrı yığını hatayla ilişkilendirilmişse çağrı yığınını **göster** bağlantısına tıklayabilirsiniz. Bu, çağrı yığınını göstermek için hatayı daha da genişletir. Yığının incelenmesiyle, değerli hata ayıklama bilgileri sağlayabilirsiniz. Örneğin, hata oluşmadan önce çağrılan işlevleri izleyebilirsiniz. Çağrı yığını seçilebilir, böylece kopyalayabilir ve kaydedebilirsiniz.

> [!NOTE]
> Visual Basic, tasarım zamanı hata listesi birden çok hata görüntülemez, ancak aynı hatanın birden fazla örneğini görüntüleyebilir. Görselde C++hatalar için goto kod bağlantıları/satır numarası bağlantıları yoktur.

### <a name="forum-posts-about-this-error"></a>Bu hatayla ilgili forum gönderileri

Ek Yardım, hatayla ilgili forum gönderileri için bir bağlantı içerir. Forumlar, hata iletisinin dizesine göre aranır. Ayrıca, aşağıdaki forumlarda aramayı deneyebilirsiniz:

- [Windows Form Tasarımcısı Forumu](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [Windows Forms Forumu](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a>Yoksay ve devam et

Hata koşulunu yoksayıp tasarımcıyı yüklemeye devam etmeyi tercih edebilirsiniz. Bu eylemi seçmek beklenmeyen davranışlara neden olabilir. Örneğin, denetimler tasarım yüzeyinde görünmeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım zamanı geliştirme sorunlarını giderme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Denetim ve Bileşen Yazmada Sorun Giderme](troubleshooting-control-and-component-authoring.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Windows Form Tasarımcısı hata Iletileri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
