---
title: .NET Derleyici Platformu SDK kavramları ve nesne modeli
description: Bu genel bakış, .NET derleyicisi SDK ile etkili bir şekilde çalışmak için gereken arka planı sağlar. API katmanlarını, ilgili ana türleri ve genel nesne modelini öğreneceksiniz.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: e563260e21fb8807017db90ff63e30fec0415a48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156967"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>.NET Derleyici Platformu SDK modelini anlayın

Derleyiciler, yazdığınız kodu, genellikle insanların kodu okuma ve anlama şeklinden farklı olan yapılandırılmış kuralları izleyerek işler. Derleyiciler tarafından kullanılan modelin temel bir şekilde anlaşılması, Roslyn tabanlı araçlar inşa ederken kullandığınız API'leri anlamak için gereklidir.

## <a name="compiler-pipeline-functional-areas"></a>Derleyici boru hattı fonksiyonel alanları

.NET Derleyici Platformu SDK, geleneksel derleyici ardışık hattını yansıtan bir API katmanı sağlayarak C# ve Visual Basic derleyicilerinin kod çözümlemesi'ni tüketici olarak size sunar.

![nesne koduna derleyici boru hattı işleme kaynak kodunun adımları](media/compiler-api-model/compiler-pipeline.png)

Bu ardışık hattın her aşaması ayrı bir bileşendir. İlk olarak, ayrıştirme aşaması, kaynak metni dil dilbilgisini izleyen sözdizimi olarak belirterek ayrıştirır. İkinci olarak, bildirim aşaması kaynak ve alınan meta verileri çözümleyip adlandırılmış sembolleroluşturur. Daha sonra, bağlama aşaması koddaki tanımlayıcıları sembollerle eşleşir. Son olarak, yayan aşama derleyici tarafından biriken tüm bilgileri içeren bir derleme yayar.

![derleyici pipeline api derleyici ardışık bir parçası olan her adıma erişim sağlar](media/compiler-api-model/compiler-pipeline-api.png)

Bu aşamaların her birine karşılık gelen .NET Derleyici Platformu SDK, o aşamadaki bilgilere erişim sağlayan bir nesne modelini ortaya çıkarır. Ayrıştırma aşaması sözdizimi ağacını, bildirim aşaması hiyerarşik bir sembol tablosunu, bağlama aşaması derleyicinin semantik çözümlemesi sonucunu ortaya çıkarır ve yaslanma aşaması IL byte kodları üreten bir API'dir.

![derleyici ardışık boru hattının her adımında derleyici api'den edinilebilen dil hizmetleri](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Her derleyici bu bileşenleri tek bir uç-uç bütün olarak birleştirir.

Bu API'ler Visual Studio tarafından kullanılanlarla aynıdır. Örneğin, kod anahat ve biçimlendirme özellikleri sözdizimi ağaçlarını kullanır, Nesne Tarayıcısı ve gezinti özellikleri sembol tablosunu kullanır, yeniden düzenleme ve Tanıma Git semantik modeli kullanır ve Düzenle ve Devam, Emit API dahil olmak üzere tüm bunları kullanır.

## <a name="api-layers"></a>API katmanları

.NET derleyici SDK API'lerin iki ana katmanından oluşur: derleyici API'leri ve çalışma alanları API'leri.

![derleyici boru hattı apistarafından temsil edilen api katmanları](media/compiler-api-model/api-layers.png)

### <a name="compiler-apis"></a>Derleyici API'leri

Derleyici katmanı, derleyici ardışık ardışık ardışık ardışık ardışık her aşamasında maruz kalan bilgilere karşılık gelen nesne modellerini içerir, hem sözdizimverici hem de anlamsal. Derleyici katmanı, derleme başvuruları, derleyici seçenekleri ve kaynak kodu dosyaları da dahil olmak üzere derleyicinin tek bir çağırmasının değişmez anlık görüntüsünü de içerir. C# dilini ve Visual Basic dilini temsil eden iki farklı API vardır. Bu iki API şeklinde benzer ama her bir dile yüksek sadakat için özel. Bu katmanın Visual Studio bileşenlerine hiçbir bağımlılığı yoktur.

### <a name="diagnostic-apis"></a>TanıSAL API'lar

Derleme, analizinin bir parçası olarak sözdizimi, anlamsal ve kesin atama hatalarından çeşitli uyarılara ve bilgilendirme diagnostiklerine kadar her şeyi kapsayan bir dizi tanılama üretebilir. Derleyici API katmanı, kullanıcı tanımlı çözümleyicilerin derleme işlemine takılmasını sağlayan genişletilebilir bir API aracılığıyla tanılamayı ortaya çıkarır. StyleCop veya FxCop gibi araçlar tarafından üretilenler gibi kullanıcı tanımlı tanılamaların derleyici tanımlı tanılamayla birlikte üretilmesine olanak tanır. Bu şekilde tanılama üretmek, politikaya dayalı bir yapıyı durdurmak ve editörde canlı squiggles göstermek ve kod önermek gibi deneyimler için tanılama ya da tanılama ya da kod önerme gibi araçlarla doğal olarak bütünleşme nin avantajına sahiptir. Giderir.

### <a name="scripting-apis"></a>Komut Dosyası API'leri

Barındırma ve komut dosyası API'leri derleyici katmanının bir parçasıdır. Bunları kod parçacıklarını yürütmek ve çalışma zamanı yürütme bağlamı biriktirmek için kullanabilirsiniz.
C# etkileşimli REPL (Oku-Değerlendir-Yazdır Döngüsü) bu API'leri kullanır. REPL, C#'ı komut dosyası dili olarak kullanmanızı ve siz yazarken kodu etkileşimli olarak yürütmenizi sağlar.

### <a name="workspaces-apis"></a>Çalışma Alanları API'leri

Çalışma Alanları katmanı, kod çözümlemesi yapmak ve tüm çözümleri yeniden düzenlemenin başlangıç noktası olan Çalışma Alanı API'sini içerir. Projelerle ilgili tüm bilgileri tek bir nesne modelinde düzenlemenize yardımcı olur ve dosyaları ayrıştırmaya, seçenekleri yapılandırmaya veya projeden projeye bağımlılıkları yönetmeye gerek kalmadan derleyici katmanı nesne modellerine doğrudan erişim sağlar .

Buna ek olarak, Çalışma Alanları katmanı, Visual Studio IDE gibi bir ana bilgisayar ortamında işlev gören kod çözümlemesi ve yeniden düzenleme araçları uygularken kullanılan bir dizi API'yi yüzeyler. Örnekler arasında Tüm Başvuruları Bul, Biçimlendirme ve Kod Oluşturma API'leri verilebilir.

Bu katmanın Visual Studio bileşenlerine hiçbir bağımlılığı yoktur.
