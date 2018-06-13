---
title: .NET derleme Platform SDK'sı kavramları ve nesne modeli
description: Bu genel bakışta .NET derleyicisi SDK ile etkin şekilde çalışması için gereken arka plan sağlar. API katmanlar, söz konusu ana türleri ve genel nesne modeli öğreneceksiniz.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: a3104313efa0110699c45a4ce7bca99aab20542a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363694"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>.NET derleme Platform SDK modelini anlama

Derleyicileri genellikle yolu insanlar farklı aşağıdaki yapılandırılmış kurallar okuyun ve kod anlamak yazma kodunu işleyin. Modelin derleyicileri tarafından kullanılan temel bir anlayış Roslyn tabanlı araçlar oluştururken kullandığınız API'leri anlamak için önemlidir. 

## <a name="compiler-pipeline-functional-areas"></a>Derleyici ardışık düzen işlevsel

.NET derleme Platform SDK'sı, geleneksel derleyici ardışık düzen yansıtan bir API katmanı sağlayarak, C# ve Visual Basic derleyicileri Kod Analizi tüketici olarak kullanıma sunar.

![nesne kodu kaynak koduna işleme derleyici ardışık adımları](media/compiler-api-model/compiler-pipeline.png)

Bu ardışık düzen her bir aşaması ayrı bir bileşendir. İlk olarak, ayrıştırma aşaması tokenizes ve kaynak metin Dili Dilbilgisi izleyen sözdizimine ayrıştırır. İkinci olarak, kaynak ve içeri aktarılan meta veri simgeleri adlı forma bildirimi aşaması çözümler. Ardından, BIND aşaması simgeleri koda tanımlayıcılarının eşleşir. Son olarak, emit aşaması derleyicisi tarafından derlenen tüm bilgileri ile bir derlemeyi yayar.

![Derleyici ardışık düzen API derleyici pipelien parçası olan her adım erişim sağlar](media/compiler-api-model/compiler-pipeline-api.png)

Her Bu aşamalar karşılık gelen, .NET derleme Platform SDK'sı bu aşamada bilgilerine erişmesini sağlayan bir nesne modeli sunar. Sözdizimi ağacı ayrıştırma aşaması gösterir, bildirimi aşaması hiyerarşik sembol tablosunu gösterir, bağlama aşaması derleyicinin semantik analizi sonucunu gösterir ve emit aşaması IL bayt kodları üreten bir API'dir.

![Derleyiciden kullanılabilen dil hizmetler derleyici ardışık her adımında API](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Her derleyici bu bileşenlerin birlikte tek bir uçtan uca bütün olarak birleştirir.

Bu API, Visual Studio tarafından kullanılan aynı olanlardır. Örneği için anahat oluşturma ve biçimlendirme özellikleri kodu sözdizimi ağaçları kullanın, Nesne Tarayıcısı ve gezinti özellikleri yapan yeniden düzenlemeler simge tablosunu kullanmak ve tanımı Git anlam modeli kullanın ve Düzenle ve devam et kullanır yayma API dahil bunların tümü. 

## <a name="api-layers"></a>API katmanları

SDK oluşan iki ana katmanları API'leri, .NET derleyici: derleyici API'leri ve çalışma alanları API'leri.

![Derleyici tarafından temsil edilen API Katmanlar API'leri kanalı](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Derleyici API'leri

Derleyici katman sözdizimsel ve anlamsal derleyici ardışık her aşamada sunulan bilgilere karşılık gelen nesne modelleri içerir. Derleyici katmanı da tek bir derleme başvurusu, derleyici seçenekleri ve kaynak kodu dosyaları dahil olmak üzere bir derleyici çalıştırılışı değişmez bir görüntüsünü içerir. C# dili ve Visual Basic dili temsil eden iki ayrı API'leri vardır. Bu iki API şeklinde benzer, ancak yüksek kaliteli her dil için tasarlanmış. Bu katman, Visual Studio bileşenlerini hiçbir bağımlılıkları vardır.

### <a name="diagnostic-apis"></a>Tanılama API'leri

Kendi analiz bir parçası olarak tanılama sözdizimi, semantik, öğrenerek ve çeşitli uyarılar ve bilgilendirici tanılama kesin atama hataları kapsayan bir dizi derleyici üretebilir. Derleyici API katmanı Tanılama kullanıcı tanımlı çözümleyiciler derleme işlemine takılı sağlayan genişletilebilir bir API aracılığıyla kullanıma sunar. Bu StyleCop veya FxCop, derleyici tanımlı tanılama üretilecek gibi araçları tarafından üretilen gibi kullanıcı tanımlı tanılama sağlar. Bu şekilde tanılama oluşturan doğal olarak MSBuild gibi araçları ile tümleştirme avantajına sahiptir ve bir yapı durdurma gibi deneyimleri için tanılama bağlı olan Visual Studio ilke ve canlı dalgalı çizgiler Düzenleyicisi'nde gösteren ve kod öneren göre giderir.

### <a name="scripting-apis"></a>Komut dosyası API'leri

Barındırma ve API scripting derleyici katman parçasıdır. Kod parçacıkları yürütme ve bir çalışma zamanı yürütme bağlamı biriktirme için bunları kullanabilirsiniz.
C# etkileşimli REPL (okuma değerlendirmek yazdırma döngü) bu API'leri kullanır. REPL siz yazarken kodu etkileşimli olarak yürütmesini C# bir komut dosyası dili kullanmanıza olanak tanır.

### <a name="workspaces-apis"></a>Çalışma alanları API'leri

Çalışma alanları katman için kod analizi yapmak ve tüm çözümleri yeniden düzenleme başlangıç noktası çalışma API içerir. Dosyaları ayrıştırma, seçeneklerini yapılandırmak gerek kalmadan derleyici katman nesnesi modellerini doğrudan erişim sunan tek nesne modeline bir çözümde proje ilgili tüm bilgileri düzenleme yardımcı olur ya da proje proje bağımlılıklarını yönetme .

Ayrıca, çalışma alanları kod çözümleme uygulama ve bir ana bilgisayar ortamında işlev araçları yeniden düzenleme Visual Studio IDE gibi bir dizi API kullanılan yüzeyleri katman. Örnekler, tüm başvuruları Bul, biçimlendirme ve kod oluşturma API içerir.

Bu katman, Visual Studio bileşenlerini hiçbir bağımlılıkları vardır.
