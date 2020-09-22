---
title: "'<filename>' çıkış dosyasına yazılamıyor: <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 73fce70c0740992e2e9159946d428d214576e163
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870288"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>'\<filename>' çıkış dosyasına yazılamıyor: \<error>

Dosya oluşturulurken bir sorun oluştu.  
  
 Çıkış dosyası yazma için açılamıyor. Dosya (veya dosyayı içeren klasör), başka bir işlem tarafından özel kullanım için açılabilir veya salt okunurdur özniteliği ayarlanmış olabilir.  
  
 Yalnızca bir dosyanın açıldığı yaygın durumlar şunlardır:  
  
- Uygulama zaten çalışıyor ve dosyalarını kullanıyor. Bu sorunu çözmek için uygulamanın çalışmadığını denetleyin.  
  
- Başka bir uygulama dosyayı açtı. Bu sorunu çözmek için, dosyalara hiçbir uygulamanın erişemdiğinizden emin olun. Dosyalarınıza hangi uygulamanın eriştiğini her zaman açık değildir; Bu durumda, bilgisayarı yeniden başlatmak uygulamayı sonlandırmak için en kolay yol olabilir.  
  
 Proje çıkış dosyalarından biri bile salt okunurdur olarak işaretlenmişse, bu özel durum oluşturulur.  
  
 **Hata kimliği:** BC31019  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Hatanın yinelenip yinelenmeyeceğini görmek için programı yeniden derleyin.  
  
2. Hata devam ederse, çalışmanızı kaydedin ve Visual Studio 'Yu yeniden başlatın.  
  
3. Hata devam ederse, bilgisayarı yeniden başlatın.  
  
4. Hata yinelenirse Visual Basic yeniden yükleyin.  
  
5. Yeniden yükleme sonrasında hata devam ederse, Microsoft Ürün Destek Hizmetleri 'ne bildirin.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Dosya Gezgini 'nde dosya özniteliklerini denetlemek için  
  
1. İlgilendiğiniz klasörü açın.  
  
2. **Görünümler** simgesine tıklayın ve **Ayrıntılar**' ı seçin.  
  
3. Sütun başlığına sağ tıklayın ve açılan listeden **öznitelikler** ' i seçin.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Bir dosya veya klasörün özniteliklerini değiştirmek için  
  
1. **Dosya Gezgini**'nde, dosya veya klasöre sağ tıklayın ve **Özellikler**' i seçin.  
  
2. **Genel** sekmesinin **öznitelikler** bölümünde **salt okunurdur** kutusunu temizleyin.  
  
3. **Tamam**'a basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bizimle iletişime geçin](/visualstudio/ide/feedback-options)
