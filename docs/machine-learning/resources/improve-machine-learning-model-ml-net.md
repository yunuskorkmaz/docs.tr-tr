---
title: 'Nasıl Yapılsın: Model doğruluğunu artırın'
description: Model doğruluğunu nasıl artırın öğrenin
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75739580"
---
# <a name="improve-mlnet-model-accuracy"></a>Model ML.NET Doğruluğunu Geliştirin

Modelinizin doğruluğunu nasıl artıreceğinizi öğrenin.

## <a name="reframe-the-problem"></a>Sorunu yeniden çerçeveleme

Bazen, bir modeli geliştirmek, modeli eğitmek için kullanılan veriler veya tekniklerle hiçbir ilgisi olmayabilir. Bunun yerine, sadece yanlış soru soruluyor olabilir. Soruna farklı açılardan bakmayı düşünün ve soruyu hassaslaştırmak için gizli göstergeleri ve gizli ilişkileri ayıklamak için verilerden yararlanın.

## <a name="provide-more-data-samples"></a>Daha fazla veri örneği sağlayın

İnsanlar gibi, daha fazla eğitim algoritmaları olsun, daha iyi performans olasılığı artar. Model performansını artırmanın bir yolu, algoritmalara daha fazla eğitim veri örnekleri sağlamaktır. Ne kadar çok veri öğrenirse, o kadar çok durumda doğru bir şekilde tanımlayabilir.

## <a name="add-context-to-the-data"></a>Verilere bağlam ekleme

Tek bir veri noktasının anlamını yorumlamak zor olabilir. Veri noktaları etrafında bağlam oluşturmak algoritmaların yanı sıra konu uzmanlarının daha iyi karar lar almesine yardımcı olur. Örneğin, bir evin üç yatak odası olması kendi başına fiyat iyi bir gösterge vermez. Ancak, bağlam eklerseniz ve şimdi ortalama yaş 38 olduğu büyük bir metropol alanı dışında bir banliyö mahallesinde olduğunu biliyorum, ortalama hane geliri 80.000 $ ve okullar ilk yüzde 20 içinde sonra algoritma tabanına daha fazla bilgi var kararlar ala. Tüm bu bağlam, makine öğrenme modeline özellik olarak girdi olarak eklenebilir.

## <a name="use-meaningful-data-and-features"></a>Anlamlı veri ve özellikler kullanma

Daha fazla veri örneği ve özelliği modelin doğruluğunu artırmaya yardımcı olsa da, tüm veriler ve özellikler anlamlı olmadığından gürültüye de neden olabilir. Bu nedenle, algoritma tarafından verilen kararları en çok etkileyen özelliklerin hangi özellikler olduğunu anlamak önemlidir. Permütasyon Özelliği Önemi (PFI) gibi tekniklerin kullanılması, bu göze çarpan özelliklerin belirlenmesine yardımcı olabilir ve yalnızca modeli açıklamaya yardımcı olmakla kalmamış, aynı zamanda eğitim sürecine giren gürültülü özelliklerin miktarını azaltmak için çıktıyı bir özellik seçim yöntemi olarak da kullanabilir.

PFI kullanma hakkında daha fazla bilgi için [bkz.](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)

## <a name="cross-validation"></a>Çapraz doğrulama

Çapraz doğrulama, verileri birkaç bölüme bölen ve bu bölümlerde birden çok algoritma eğiten bir eğitim ve model değerlendirme tekniğidir. Bu teknik, eğitim sürecinden verileri tutarak modelin sağlamlığını artırır. Görünmeyen gözlemlerde performansı artırmanın yanı sıra, veri kısıtlamalı ortamlarda daha küçük bir veri kümesine sahip modelleri eğitmek için etkili bir araç olabilir.

ML.NET çapraz [doğrulamayı nasıl kullanacağınızı](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) öğrenmek için aşağıdaki bağlantıyı ziyaret edin

## <a name="hyperparameter-tuning"></a>Hiper parametre ayarı

Eğitim makine öğrenme modelleri yinelemeli ve araştırmacı bir süreçtir. Örneğin, K-Means algoritmasını kullanarak bir modeli eğitirken en uygun küme sayısı nedir? Yanıt, verilerin yapısı gibi birçok etkene bağlıdır. Bu sayıyı bulmak için k için farklı değerler deneme ve ardından hangi değerin en iyi olduğunu belirlemek için performansı değerlendirmek gerekir. En uygun modeli bulmak için bu parametreleri ayarı uygulaması hiper-parametre ayarı olarak bilinir.

## <a name="choose-a-different-algorithm"></a>Farklı bir algoritma seçin

Regresyon ve sınıflandırma gibi makine öğrenimi görevleri çeşitli algoritma uygulamaları içerir. Çözmeye çalıştığınız sorun ve verilerinizin yapılandırılması durumu geçerli algoritmaya uymuyor olabilir. Bu durumda, verilerinizden daha iyi öğrenip öğrenmeyişini görmek için göreviniz için farklı bir algoritma kullanmayı düşünün.

Aşağıdaki [bağlantı, hangi algoritmanın seçilen](../how-to-choose-an-ml-net-algorithm.md)hakkında daha fazla kılavuz sağlar.
