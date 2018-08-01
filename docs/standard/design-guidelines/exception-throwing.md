---
title: Özel durum atma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a493e6591d90ce05a652e48807f63fa90764a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573727"
---
# <a name="exception-throwing"></a>Özel durum atma
Bu bölümde açıklanan özel durum atma yönergeleri yürütme hatası anlamını iyi tanımının gerektirir. Yürütme hatası oluşursa üyesi ne olduğunu yapamayacağı her (ne üye adından da anlaşılacağı) yapmak için tasarlanmıştır. Örneğin, varsa `OpenFile` yöntemi bir açılan dosya tanıtıcısı çağırana döndüremiyor, bir yürütme hatası kabul edilmesi.  
  
 Çoğu geliştirici özel durumlar bölme gibi kullanım hatalar için sıfır ya da null başvurular kullanabileceğinizden hale getirildi. Framework'te özel durumları yürütme hatalar dahil olmak üzere tüm hata koşulları için kullanılır.  
  
 **X DO NOT** hata kodlarını döndürür.  
  
 İstisnaları çerçeveleri hatalarını raporlama birincil anlamına gelir.  
  
 **✓ DO** rapor yürütme hataları özel durumları atma.  
  
 **✓ CONSIDER** çağırarak işlem sonlandırılıyor `System.Environment.FailFast` (.NET Framework 2.0 özelliği) kodunuzu daha fazla yürütme için güvenli olduğu bir durumla karşılaşırsa yerine bir özel durum atma.  
  
 **X DO NOT** özel durumlar için normal akışı denetimi, mümkünse kullanın.  
  
 Kullanıcıların özel durumlar oluşturmadığını kod yazabilirsiniz şekilde sistem hataları ve olası yarış durumlarını işlemleriyle dışında framework tasarımcıları API'leri tasarlamanız gerekir. Örneğin, kullanıcıların özel durumlar oluşturmadığını kod yazabilirsiniz şekilde üyesi çağırmadan önce önkoşulları kontrol etmenin bir yolu sağlayabilir.  
  
 Başka bir üyesinin önkoşulları denetlemek için kullanılan üye genellikle tester adlandırılır ve gerçekte çalışır üye bir doer çağrılır.  
  
 Kabul edilebilir bir performansa Tester Doer düzeni olabilir, durumlar vardır. Böyle durumlarda, sözde deneyin ayrıştırma düzeni bulundurulması gerekir (bkz [özel durumları ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) daha fazla bilgi için).  
  
 **✓ CONSIDER** özel durumları atma performans etkileri. Throw hızlarını saniyede 100 yukarıda büyük bir olasılıkla çoğu uygulamalarının performansını önemli ölçüde etkileyebilir.  
  
 **✓ DO** belge herkese açık şekilde çağrılabilir üyeleri tarafından bir üye ihlali nedeniyle oluşturulan tüm özel durumları Sözleşme (bir sistem hatası yerine) ve bunları sizin sözleşmesinin bir parçası davran.  
  
 Sözleşmenin parçası olan özel durumlar değiştirme bir sürümünden sonraki (yani, özel durum türü değiştirme ve yeni özel durumlar eklenmemelidir).  
  
 **X DO NOT** olması ya da throw veya yok edebilir Genel üyeler temel bazı seçeneği.  
  
 **X DO NOT** dönüş değeri olarak özel durumları döndüren Genel üyeler olması veya bir `out` parametresi.  
  
 Bunları atma yerine ortak API'ler özel durumlar döndürme birçok özel durum tabanlı hata raporlama avantajı defeats.  
  
 **✓ CONSIDER** özel Oluşturucu yöntemleri kullanarak.  
  
 Farklı yerlerden aynı özel durum yaygındır. Kod oluşan şişirmeyi önlemek için özel durumlar oluşturma ve bunların özelliklerini başlatma yardımcı yöntemlerini kullanın.  
  
 Ayrıca, özel durumlar oluşturma üyeleri değil aldıklarından içermesinden. Throw deyimi oluşturucu içinde taşıma üye içermesinden olmasını sağlayabilir.  
  
 **X DO NOT** özel durum filtresi taşlarından özel durumlar oluşturma.  
  
 Bir özel durum filtresi bir özel durum oluşturur, CLR tarafından özel durum yakalandı ve filtre false döndürür. Bu davranış yürütme ve açıkça false değerinin döndürülmesi filtresinden ayırt ve bu nedenle hata ayıklamak çok zordur.  
  
 **X AVOID** açıkça finally blokları özel durumları atma. Throw yöntemleri çağırma sonucu oluşan örtük olarak atılmış özel durumları kabul edilir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Özel Durumlar için Tasarım Yönergeleri](../../../docs/standard/design-guidelines/exceptions.md)
