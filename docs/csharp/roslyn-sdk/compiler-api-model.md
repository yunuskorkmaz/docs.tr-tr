---
title: .NET derleyici Platformu SDK'sı kavramları ve nesne modeli
description: .NET derleyici SDK'sı ile etkili bir şekilde çalışması için gereken arka plan bu genel bakış sağlar. API katmanları, ilgili önemli türleri ve genel nesne modeli öğreneceksiniz.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: ee8f902bf1df8b63e229fd518e7a0c592fcd47ca
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675712"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>.NET derleyici Platformu SDK'sı modelini anlama

Derleyiciler, şekilde insanlar genellikle farklı aşağıdaki yapılandırılmış kuralları okuma ve kod anlama yazdığınız kod işleyin. Derleyiciler tarafından kullanılan modelini temel bir anlayış, Roslyn tabanlı araçlar oluştururken kullandığınız API'leri anlamak için gereklidir. 

## <a name="compiler-pipeline-functional-areas"></a>Derleme işlem hattı işlevsel alanları

.NET derleyici Platformu SDK'sı sunan C# ve Visual Basic derleyicileri, geleneksel derleme işlem hattı yansıtan bir API katmanı sağlayarak kullanıcı olarak analysis size kod.

![nesne kodu için kaynak kodu işleme derleyici Ardışık düzenin adımları](media/compiler-api-model/compiler-pipeline.png)

Bu Ardışık düzenin her aşaması ayrı bir bileşendir. İlk olarak, ayrıştırma aşaması tokenizes ve kaynak metni dil dilbilgisi aşağıdaki sözdizimine ayrıştırır. İkinci olarak, bildirimi aşaması, kaynak ve simgeleri adlı forma alınan meta verileri analiz eder. Ardından, bağlama aşaması kodu sembol tanımlayıcıları eşleşir. Son olarak, emit aşaması derleyicisi tarafından derlenen tüm bilgileri içeren bir bütünleştirilmiş kod yayar.

![derleme işlem hattı API derleyici işlem hattının bir parçası olan her adım için erişim sağlar](media/compiler-api-model/compiler-pipeline-api.png)

.NET derleyici Platformu SDK'sı, bu aşamaların her birine karşılık gelen, bu aşamada bilgilerine erişmesine izin veren bir nesne modeli sunar. Ayrıştırma aşaması söz dizimi ağacı kullanıma sunar, bildirimi aşaması hiyerarşik sembol tablosu kullanıma sunar, bağlama aşaması, derleyicinin anlam çözümleme sonucu kullanıma sunar ve emit aşaması IL bayt kodları üreten bir API'dir.

![Derleyiciden kullanılabilir dil Hizmetleri API derleyici işlem hattının her bir adımı](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Her derleyici bu bileşenlerin tek uçtan uca bir bütün olarak birleştirir.

Bu API'ler, Visual Studio tarafından kullanılan aynı olanlardır. Örneği için anahat oluşturma ve biçimlendirme özellikleri kod söz dizimi ağacı kullanın, sembol tablosu, yeniden düzenlemeler Nesne Tarayıcısı ve gezinti özelliklerini kullanmak ve Tanıma Git anlam modeli kullanın ve Düzenle ve devam et kullanır yayma API dahil olmak üzere bunların tümü. 

## <a name="api-layers"></a>API katmanları

.NET derleyici SDK'sı API'leri iki ana katman oluşur: derleyici API'leri ve çalışma alanları API'leri.

![Derleyici tarafından temsil edilen API katmanları API'leri işlem hattı](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Derleyici API'leri

Derleyici katman sözdizimsel ve semantik derleyici işlem hattının her aşamada kullanıma sunulan bilgilere karşılık gelen nesne modellerini içerir. Derleyici katmanın, tek bir çağrı derleme başvuruları, derleyici seçenekleri ve kaynak kodu dosyaları gibi bir derleyici değişmez bir anlık görüntüsünü de içerir. Temsil eden iki ayrı API vardır C# dil ve Visual Basic dili. Bu iki API şeklinde benzerdir ancak her dil için yüksek kaliteli için uyarlanmış. Bu katman, Visual Studio bileşenlerini bağımlılık yok.

### <a name="diagnostic-apis"></a>Tanılama API'leri

Kendi analiz bir parçası olarak, derleyici tanılama söz dizimi, semantik, kadar her şeyi ve çeşitli uyarılar ve bilgilendirici tanılama kesin atama hataları kapsayan bir dizi üretebilir. Derleyici API katmanı Tanılama kullanıcı tanımlı Çözümleyicileri derleme işlemine takılı sağlayan genişletilebilir bir API aracılığıyla sunar. Kullanıcı tanımlı StyleCop ya da FxCop, derleyici tarafından tanımlanan tanılama yanı sıra üretilecek gibi araçlar tarafından üretilen olanlar gibi tanılama sağlar. Bu şekilde tanılama üretme doğal olarak MSBuild gibi araçlarla tümleştirme avantajına sahiptir ve tanılama için bir yapıyı durdurma gibi deneyimleri bağımlı Visual Studio İlkesi ve düzenleyicide Canlı dalgalı çizgiler gösteren kod önerme tabanlı ve düzeltir.

### <a name="scripting-apis"></a>Betik yazma API'leri

Barındırma ve betik yazma API'leri derleyici katman parçasıdır. Kod parçacıkları yürütülüyor ve bir çalışma zamanı yürütme bağlamı biriktirme için bunları kullanabilirsiniz.
C# Etkileşimli REPL (okuma değerlendirmek yazdırma döngü) bu API'lerini kullanır. REPL kullanmanızı sağlayan C# yazmanız gibi bir komut dosyası dili kod etkileşimli olarak çalıştırmak.

### <a name="workspaces-apis"></a>Çalışma alanları API'leri

Çalışma alanları katman tüm çözümleri yeniden düzenleme ve kod analizi yapmak için başlangıç noktası olan çalışma API içerir. Tek nesne modeline gerek kalmadan seçeneklerini yapılandırma dosyalarını ayrıştırmak derleyici katman nesnesi modellerini doğrudan erişim sunan bir çözüm içindeki projeleri hakkındaki tüm bilgileri düzenleme yönetmenize yardımcı olan veya projeden projeye bağımlılıkları yönetin .

Ayrıca, çalışma alanlarını Kod Analizi uygulaması ve bir ana bilgisayar ortamının içinde işlev araçları yeniden düzenleme, Visual Studio IDE gibi bir API kümesi kullanılan yüzeyleri katman. Tüm başvuruları Bul, biçimlendirme ve kod oluşturma API'ları verilebilir.

Bu katman, Visual Studio bileşenlerini bağımlılık yok.
