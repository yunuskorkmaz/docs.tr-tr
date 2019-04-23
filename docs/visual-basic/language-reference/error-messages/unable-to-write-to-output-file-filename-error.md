---
title: "'<filename>' çıkış dosyasına yazılamıyor: <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: f29eb628c079f65a520cf5e1ccd8afed549f7cad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318227"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>Çıkış dosyasına yazılamıyor '\<dosya adı >': \<hata >
Dosya oluşturulurken bir sorun oluştu.  
  
 Bir çıkış dosyası yazma için açılamıyor. Başka bir işlem tarafından özel kullanım için dosya (veya dosyasını içeren klasör) açılabilir veya salt okunur özniteliğini ayarlayın olabilir.  
  
 Burada bir dosya özel olarak açılmış yaygın durumlar şunlardır:  
  
-   Uygulama zaten çalışıyor ve dosyalarını kullanarak. Bu sorunu çözmek için uygulamayı çalışır durumda olduğundan emin olun.  
  
-   Başka bir uygulama, dosya açıldı. Bu sorunu çözmek için başka bir uygulama dosyaları eriştiğinden emin olun. Her zaman uygulama dosyalarınızı erişiyor belirgin değildir; Bu durumda, bilgisayarı yeniden başlatmadan uygulamayı sonlandırmak için en kolay yolu olabilir.  
  
 Proje çıktı dosyalarını biri bile salt okunur olarak işaretlenmişse, bu özel durum oluşturulur.  
  
 **Hata Kimliği:** BC31019  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yinelenen hata durumunda yeniden görmek için programı derleyin.  
  
2. Hata devam ederse, çalışmanızı kaydedin ve Visual Studio'yu yeniden başlatın.  
  
3. Hata devam ederse bilgisayarı yeniden başlatın.  
  
4. Hata almaya devam ederseniz, Visual Basic yeniden yükleyin.  
  
5. Yeniden yüklenmesinden sonra hata oluşmaya devam ederse Microsoft Ürün Destek Hizmetleri bildirin.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Dosya Gezgini'nde dosya özniteliklerini kontrol etmek için  
  
1. İlgilendiğiniz klasörünü açın.  
  
2. Tıklayın **görünümleri** simgesini seçip **ayrıntıları**.  
  
3. Sütun üst bilgisine sağ tıklayın ve seçin **öznitelikleri** aşağı açılan listeden.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Bir dosya veya klasör özniteliklerini değiştirmek için  
  
1. İçinde **dosya Gezgini**, dosya veya klasörü sağ tıklatın ve seçin **özellikleri**.  
  
2. İçinde **öznitelikleri** bölümünü **genel** sekmesi, NET **salt okunur** kutusu.  
  
3. Tuşuna **Tamam**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
