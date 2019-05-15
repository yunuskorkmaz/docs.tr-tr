---
title: 'Nasıl yapılır: Model doğruluğunu artırma'
description: Model doğruluğunu artırmayı öğrenin
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8bb47102ede8e135090b1381eb815dccd512e03d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557796"
---
# <a name="improve-mlnet-model-accuracy"></a>ML.NET Model doğruluğunu artırmak

Modelinizi doğruluğunu artırmak öğrenin.

## <a name="reframe-the-problem"></a>Sorun reframe

Bazı durumlarda, bir model geliştirme veri veya modeli eğitmek için kullanılan teknikleri ile ilgisi olabilir. Bunun yerine, yanlış sorunun sorulmaktadır yalnızca olabilir. Farklı açıları soruna bakış göz önünde bulundurun ve soru iyileştirmek için görünmeyen göstergeleri ve ilişkileri ayıklanacak veri yararlanın.

## <a name="provide-more-data-samples"></a>Daha fazla veri örnekleri sağlar

İnsanlar gibi daha fazla eğitim algoritmalar Al, daha iyi performans artışı olasılığını. Model performansını artırmanın bir yolu, daha fazla eğitim veri örnekleri algoritmalar sağlamaktır. Daha fazla veri bunu, daha fazla durumlarda düzgün tanımlayamayabilir öğrenir.

## <a name="add-context-to-the-data"></a>Veri bağlamı Ekle

Tek bir veri noktasının anlamını yorumlamak zor olabilir. Veri noktaları etrafında bağlam oluşturma algoritmaları ve bunun yanı sıra daha iyi kararlar konu uzmanları yardımcı olur. Örneğin, bir ev üç yatak sahip olmasına değil kendi başına bir göstergesidir kendi fiyatının verin. Ancak bağlam ekleyin ve ortalama yaş 38 olduğu büyük bir metropol alanı dışında banliyöde yaşayan bir Komşuları içinde olduğunu biliyorsunuz, ortalama hane halkı geliri $80.000 ve okullar en çok 20 yüzdelik dilim temel için daha fazla bilgi algoritma varsa, kararları. Bu bağlamın tüm machine learning modeli giriş olarak özellikleri eklenebilir.

## <a name="use-meaningful-data-and-features"></a>Anlamlı veri ve özelliklerini kullanma

Daha fazla veri örnekleri ve özellik, modelin doğruluğunu iyileştirmeye yardımcı olabilecek olsa da, bunlar aynı zamanda tüm veriler paraziti ve özellikleri anlamlı. Bu nedenle, hangi özelliklerinin en çok etkisi kararları algoritma tarafından yapılan ayarlara olduğunu anlama açısından önemlidir. PERMÜTASYON özellik önem derecesi (PFI) gibi teknikler kullanılarak bu dikkat çekici özellikleri tanımlamaya yardımcı olmak ve yalnızca model açıklanmasına yardımcı ancak ayrıca çıktısı eğitim işlemine geçmeden gürültülü özellikleri miktarını azaltmak için özellik seçimi yöntemi olarak kullanın.

Aşağıdaki ziyaret ederek PFI kullanmayı öğrenme [bağlantı](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)

## <a name="cross-validation"></a>Çapraz doğrulama

Çapraz doğrulama, eğitim ve veriler çeşitli bölümlere ayırır ve bu bölümler birden çok algoritmalarına eğitir model değerlendirme teknik ' dir. Bu teknik, eğitim işlem verileri tutarak modelinin sağlamlık artırır. Görünmeyen gözlemler performans iyileştirme yanı sıra veri kısıtlı ortamlarında, daha küçük bir veri kümesiyle eğitim modelleri için etkili bir aracı olabilir.

Bilgi edinmek için aşağıdaki bağlantıyı ziyaret edin [ML.NET çapraz doğrulama kullanma](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>Hiper parametre ayarı

Eğitim makine öğrenimi modellerini yinelemeli ve keşif bir işlemdir. Örneğin, en uygun sayıda kümeleri K-ortalamaları algoritmasını kullanarak bir modeli eğitimindeki nedir? Yanıt veri yapısı gibi birçok faktöre bağlıdır. Sayı k için farklı değerler denemeler yapmaya ve ardından hangi değerin en iyi olduğunu belirlemek için performans değerlendirmesi gerektirecek bulma. En iyi bir model bulmak için şu parametreleri ayarlama uygulaması hyper parametresi ayarlama olarak bilinir.

## <a name="choose-a-different-algorithm"></a>Farklı bir algoritma seçme

Makine öğrenimi görevlerini regresyon ve sınıflandırma gibi çeşitli algoritması uygulamalarını içerir. Bu sorunu çözmeye çalışıyorsanız ve verilerinizi yapılandırılmış bir şekilde de algoritma uymuyor durumda olabilir. Böyle bir durumda, bunu daha iyi verilerinizden öğrenir, görmek için farklı bir algoritma göreviniz için kullanmayı düşünün.

Aşağıdaki bağlantıda daha fazla bilgi sağlayan [algoritmayı seçmek için yönergeler](../how-to-choose-an-ml-net-algorithm.md).
