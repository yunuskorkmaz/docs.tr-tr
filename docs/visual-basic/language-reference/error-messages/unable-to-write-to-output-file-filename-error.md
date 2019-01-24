---
title: 'Çıkış dosyasına yazılamıyor &#39; &lt;filename&gt;&#39;: &lt;hata&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: c82f1e6e4a01af87cc7dce49cfaa78f9be1631db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572701"
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a>Çıkış dosyasına yazılamıyor &#39; &lt;filename&gt;&#39;: &lt;hata&gt;
Dosya oluşturulurken bir sorun oluştu.  
  
 Bir çıkış dosyası yazma için açılamıyor. Başka bir işlem tarafından özel kullanım için dosya (veya dosyasını içeren klasör) açılabilir veya salt okunur özniteliğini ayarlayın olabilir.  
  
 Burada bir dosya özel olarak açılmış yaygın durumlar şunlardır:  
  
-   Uygulama zaten çalışıyor ve dosyalarını kullanarak. Bu sorunu çözmek için uygulamayı çalışır durumda olduğundan emin olun.  
  
-   Başka bir uygulama, dosya açıldı. Bu sorunu çözmek için başka bir uygulama dosyaları eriştiğinden emin olun. Her zaman uygulama dosyalarınızı erişiyor belirgin değildir; Bu durumda, bilgisayarı yeniden başlatmadan uygulamayı sonlandırmak için en kolay yolu olabilir.  
  
 Proje çıktı dosyalarını biri bile salt okunur olarak işaretlenmişse, bu özel durum oluşturulur.  
  
 **Hata Kimliği:** BC31019  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Yinelenen hata durumunda yeniden görmek için programı derleyin.  
  
2.  Hata devam ederse, çalışmanızı kaydedin ve Visual Studio'yu yeniden başlatın.  
  
3.  Hata devam ederse bilgisayarı yeniden başlatın.  
  
4.  Hata almaya devam ederseniz, Visual Basic yeniden yükleyin.  
  
5.  Yeniden yüklenmesinden sonra hata oluşmaya devam ederse Microsoft Ürün Destek Hizmetleri bildirin.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Dosya Gezgini'nde dosya özniteliklerini kontrol etmek için  
  
1.  İlgilendiğiniz klasörünü açın.  
  
2.  Tıklayın **görünümleri** simgesini seçip **ayrıntıları**.  
  
3.  Sütun üst bilgisine sağ tıklayın ve seçin **öznitelikleri** aşağı açılan listeden.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Bir dosya veya klasör özniteliklerini değiştirmek için  
  
1.  İçinde **dosya Gezgini**, dosya veya klasörü sağ tıklatın ve seçin **özellikleri**.  
  
2.  İçinde **öznitelikleri** bölümünü **genel** sekmesi, NET **salt okunur** kutusu.  
  
3.  Tuşuna **Tamam**.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
