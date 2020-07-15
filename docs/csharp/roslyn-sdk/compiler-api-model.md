---
title: SDK kavramlarını ve nesne modelini .NET Compiler Platform
description: Bu genel bakış, .NET derleyici SDK 'Sı ile etkin şekilde çalışmanız için gereken arka planı sağlar. API katmanlarını, ilgili ana türleri ve genel nesne modelini öğreneceksiniz.
ms.date: 07/13/2020
ms.custom: mvc
ms.openlocfilehash: a65d282dd3c58279bbfd635c0386d50ce3f30055
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374474"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>.NET Compiler Platform SDK modelini anlama

Derleyiciler, genellikle, insanların kodu okumasından ve anlayacağından farklı şekilde yazdığınız yapılandırılmış kurallara göre yazdığınız kodu işler. Derleyiciler tarafından kullanılan modelin temel olarak anlaşılmasına, Roslyn tabanlı araçlar oluştururken kullandığınız API 'Leri anlamak önemlidir.

## <a name="compiler-pipeline-functional-areas"></a>Derleyici ardışık düzeni işlevsel alanı

.NET Compiler Platform SDK, geleneksel bir derleyici işlem hattını yansıtan bir API katmanı sağlayarak C# ve Visual Basic derleyicilerinin Kod analizini bir tüketici olarak kullanıma sunar.

![Derleyici işlem hattının, nesne koduna işleme kaynak kodu adımları](media/compiler-api-model/compiler-pipeline.png)

Bu işlem hattının her aşaması ayrı bir bileşendir. İlk olarak, ayrıştırma aşaması, kaynak metnini simgeleştirir ve dil dilbilgisini izleyen söz dizimine ayrıştırır. İkinci olarak, bildirim aşaması, adlandırılmış sembolleri biçimlendirmek için kaynağı ve içeri aktarılan meta verileri analiz eder. Sonra, bağlama aşaması koddaki tanımlayıcılarla eşleşir. Son olarak, yayma aşaması derleyici tarafından oluşturulan tüm bilgileri içeren bir derleme yayar.

![Derleyici ardışık düzeni API 'si, derleyici ardışık düzeninin parçası olan her adıma erişim sağlar](media/compiler-api-model/compiler-pipeline-api.png)

Bu aşamaların her birine karşılık gelen .NET Compiler Platform SDK, söz konusu aşamadaki bilgilere erişim sağlayan bir nesne modeli sunar. Ayrıştırma aşaması bir sözdizimi ağacı sunar, bildirim aşaması hiyerarşik bir sembol tablosu gösterir, bağlama aşaması derleyicinin anlam analizinin sonucunu gösterir ve yayma aşaması, IL bayt kodları üreten bir API 'dir.

![Derleyici işlem hattının her adımında derleyici API 'sinde kullanılabilen dil Hizmetleri](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Her derleyici bu bileşenleri tek bir uçtan uca tam olarak birleştirir.

Bu API 'Ler, Visual Studio tarafından kullanılan aynı olanlardır. Örneğin, kod ana hattı ve biçimlendirme özellikleri, sözdizimi ağaçlarını, **nesne tarayıcısı**ve gezinti özelliklerini kullanır, yeniden düzenlemeler ve **Açıklama ' ya git** , anlam modelini kullanır ve **Düzenle ve devam et** , yayma API 'si de dahil olmak üzere tümünü kullanır.

## <a name="api-layers"></a>API katmanları

.NET derleyici SDK 'Sı birçok API katmanından oluşur: derleyici API 'Leri, tanılama API 'leri, betik API 'leri ve çalışma alanı API 'Leri.

### <a name="compiler-apis"></a>Derleyici API 'Leri

Derleyici katmanı, derleyici ardışık düzeninin her aşamasında gösterilen bilgilere karşılık gelen nesne modellerini, hem sözdizimsel hem de anlam içerir. Derleyici katmanı, derleme başvuruları, derleyici seçenekleri ve kaynak kodu dosyaları da dahil olmak üzere tek bir derleyici çağrısının sabit bir anlık görüntüsünü içerir. C# dilini ve Visual Basic dilini temsil eden iki ayrı API vardır. İki API, şekille benzerdir ancak her bir dil için yüksek uygunluğa göre tasarlanmıştır. Bu katmanın Visual Studio bileşenlerinde hiçbir bağımlılığı yoktur.

### <a name="diagnostic-apis"></a>Tanılama API 'Leri

Analizinin bir parçası olarak, derleyici söz dizimi, anlam ve belirli atama hatalarından her şeyi kapsayan bir tanılama kümesi oluşturabilir ve çeşitli uyarılar ve bilgilendirici tanılamaları olabilir. Derleyici API katmanı, Kullanıcı tanımlı çözümleyiciler derleme sürecine takılmasına olanak sağlayan genişletilebilir bir API aracılığıyla tanılamayı kullanıma sunar. StyleCop veya FxCop gibi araçlarla üretilenler gibi Kullanıcı tanımlı tanılamaları, derleyici tanımlı tanılamalarıyla birlikte üretilede sağlar. Tanılamayı bu şekilde oluşturmak, MSBuild ve Visual Studio gibi araçlarla doğal olarak tümleştirmenin avantajına sahiptir. Bu, ilkeye dayalı bir derlemeyi durdurma ve düzenleyicide canlı dalgalı çizgiler gösterme ve kod düzeltmeleri önerme gibi deneyimlere bağlı olan bir deneyim tanımasına bağlıdır.

### <a name="scripting-apis"></a>Betik oluşturma API 'Leri

Barındırma ve betik oluşturma API 'Leri, derleyici katmanının bir parçasıdır. Bunları kod parçacıklarını yürütmek ve bir çalışma zamanı yürütme bağlamını biriktirme amacıyla kullanabilirsiniz.
C# etkileşimli REPL (Read-değerlendir-Print döngüsü) Bu API 'Leri kullanır. REPL, C# ' yi bir komut dosyası dili olarak kullanmanızı sağlar ve kodu yazarken etkileşimli olarak çalıştırabilirsiniz.

### <a name="workspaces-apis"></a>Çalışma alanları API 'Leri

Çalışma alanları katmanı, Kod analizini yapmak ve tüm çözümlerin yeniden düzenlemesi için başlangıç noktası olan çalışma alanı API 'sini içerir. Bir çözümdeki projelerle ilgili tüm bilgileri tek bir nesne modeline göre organize etmek için size yardımcı olur. Bu, dosyaları ayrıştırmaya, seçenekleri yapılandırmanıza veya projeden projeye bağımlılıkları yönetmeye gerek kalmadan derleyici katmanı nesne modellerine doğrudan erişmenizi sağlar.

Ayrıca, çalışma alanları katmanı, Visual Studio IDE gibi bir konak ortamında işlev Analizi ve yeniden düzenleme araçları uygularken kullanılan bir API kümesini yüzey halinde gösterir. Örnekler, tüm başvuruları bul, biçimlendirme ve kod oluşturma API 'Lerini içerir.

Bu katmanın Visual Studio bileşenlerinde hiçbir bağımlılığı yoktur.
