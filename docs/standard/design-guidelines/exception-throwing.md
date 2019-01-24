---
title: Özel durum
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: KrzysztofCwalina
ms.openlocfilehash: 74eee418a3c87b335cdf96557c4e17b95aff7b58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562888"
---
# <a name="exception-throwing"></a>Özel durum
Bu bölümde açıklanan özel durum atma yönergeleri iyi bir anlamı yürütme hatası tanımı gerektirir. Üyesi ne olduğunu yapamayacağınız her yürütme hatası meydana gelir (ne üye adından da anlaşılacağı) yapmak için tasarlanmıştır. Örneğin, varsa `OpenFile` bir yürütme hatası değerlendirilebilecek, metodu çağırana bir açık dosya tanıtıcısı döndüremiyor.  
  
 Çoğu geliştirici, özel durumlar bölme gibi kullanım hataları için sıfır ya da null başvuru kullanabileceğinizden haline geldi. Framework, özel durumları, yürütme hataları dahil olmak üzere tüm hata koşulları için kullanılır.  
  
 **X DO NOT** hata kodlarını döndürür.  
  
 Özel durumları, hataları çerçeveleri raporlama birincil araçlarıdır.  
  
 **✓ DO** rapor yürütme hataları özel durumları atma.  
  
 **✓ CONSIDER** çağırarak işlem sonlandırılıyor `System.Environment.FailFast` (.NET Framework 2.0 özelliği) kodunuzu daha fazla yürütme için güvenli olduğu bir durumla karşılaşırsa yerine bir özel durum atma.  
  
 **X DO NOT** özel durumlar için normal akışı denetimi, mümkünse kullanın.  
  
 Kullanıcıların özel durum oluşturmadığını kod yazabilmesi sistem hataları ve olası yarış durumlarını işlemleriyle dışında framework tasarımcıları API'leri tasarlamanız gerekir. Örneğin, kullanıcılar özel durum oluşturmadığını kod yazabilmesi üyesi çağırmadan önce önkoşulları denetleme olanağı sağlayabilir.  
  
 Başka bir üyesinin önkoşulları denetlemek için kullanılan bir üye genellikle test edici adlandırılır ve iş yapan üye bir doer çağrılır.  
  
 Test edici Doer desenini kabul edilemez bir performansa sahip olabilir, durumlar vardır. Bu gibi durumlarda sözde deneyin-ayrıştırma desenindeki düşünülmesi gereken (bkz [özel durumlar ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) daha fazla bilgi için).  
  
 **✓ CONSIDER** özel durumları atma performans etkileri. Saniye başına 100'ün üzerinde throw oranları, çoğu uygulama performansı önemli ölçüde etkiler olasılığı düşüktür.  
  
 **✓ DO** belge herkese açık şekilde çağrılabilir üyeleri tarafından bir üye ihlali nedeniyle oluşturulan tüm özel durumları Sözleşme (bir sistem hatası yerine) ve bunları sizin sözleşmesinin bir parçası davran.  
  
 Sözleşmenin bir parçası olan özel durumlar sonraki bir sürümü değil değiştirilmelidir (yani, özel durum türü değiştirme ve yeni özel durumlar eklenmemelidir).  
  
 **X DO NOT** olması ya da throw veya yok edebilir Genel üyeler temel bazı seçeneği.  
  
 **X DO NOT** dönüş değeri olarak özel durumları döndüren Genel üyeler olması veya bir `out` parametresi.  
  
 Özel durumlar, bunları atma yerine genel API'ler döndürme özel durum tabanlı hata raporlama avantajlarının birçoğundan faydalanılmasını boşa çıkarır.  
  
 **✓ CONSIDER** özel Oluşturucu yöntemleri kullanarak.  
  
 Farklı yerlerden aynı durum yaygındır. Kod Şişirme önlemek için özel durumlar oluşturma ve bunların özelliklerini başlatır yardımcı yöntemler kullanın.  
  
 Ayrıca, özel durumlar üyeleri değil alıyorsanız satır içine alınmış. Throw deyimi oluşturucu içinde taşıma, satır içine alınmayacak kadar üye izin vermeyi seçebilir.  
  
 **X DO NOT** özel durum filtresi taşlarından özel durumlar oluşturma.  
  
 Özel durum filtresi özel durum harekete, CLR tarafından özel durum yakalandı ve filtre false döndürür. Bu davranış yürütme ile açıkça false döndüren filtresinden sihirden ve bu nedenle hata ayıklama oldukça zor.  
  
 **X AVOID** açıkça finally blokları özel durumları atma. Throw yöntemleri çağırma özel durumlar oluşturulduğunda örtük olarak kabul edilir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)
