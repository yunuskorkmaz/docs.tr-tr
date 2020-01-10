---
title: 'Nasıl yapılır: model doğruluğunu Iyileştirme'
description: Model doğruluğunu geliştirme hakkında bilgi edinin
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739580"
---
# <a name="improve-mlnet-model-accuracy"></a>ML.NET model doğruluğunu geliştirme

Modelinizin doğruluğunu nasıl artıracağınızı öğrenin.

## <a name="reframe-the-problem"></a>Sorunu reframe

Bazen bir modelin geliştirilmesi, modeli eğmekte kullanılan veriler veya tekniklerle ilgili hiçbir şey yapmayabilir. Bunun yerine, yalnızca yanlış soru soruyor olabilir. Sorunu farklı açılardan göz önünde bulundurun ve soruyu iyileştirmek için, görünmeyen göstergeleri ve gizli ilişkileri ayıklamak için verilerden yararlanın.

## <a name="provide-more-data-samples"></a>Daha fazla veri örneği sağlayın

İnsanlar gibi eğitim algoritmaları arttıkça, daha iyi performans olasılığı da artar. Model performansını artırmanın bir yolu, algoritmalara daha fazla eğitim veri örneği sağlamaktır. Daha fazla veri öğrendiğinde, daha fazla durum doğru şekilde tespit edebilecektir.

## <a name="add-context-to-the-data"></a>Verilere bağlam ekleyin

Tek bir veri noktasının anlamı yorumlamak zor olabilir. Veri noktaları çevresinde derleme bağlamı, algoritmaların yanı sıra konuyla ilgili uzmanların daha fazla kararlar almasına yardımcı olur. Örneğin, bir evin üç yatak odaya sahip olması, kendi fiyatına uygun bir gösterge sunmasıdır. Bununla birlikte, bağlam eklerseniz ve artık ortalama yaş 38, ortalama ana bilgisayarın geliri $80.000 ve okulların en fazla 20 ' nin üst 20 ' de olduğu bir alt şehir içinde olduğunu biliyorsanız, algoritmanın kararlar. Bu bağlamın hepsi, makine öğrenimi modeline, özellikler olarak girdi olarak eklenebilir.

## <a name="use-meaningful-data-and-features"></a>Anlamlı veri ve özellikler kullanın

Daha fazla veri örneği ve özellik modelin doğruluğunu iyileştirebilse de, tüm veriler ve Özellikler anlamlı olmadığından gürültü de getirebilir. Bu nedenle, algoritma tarafından yapılan kararların en fazla etkisi olan özellikleri anlamak önemlidir. Permütasyon özelliği önem derecesi (PFI) gibi tekniklerin kullanılması, bu önemli özellikleri belirlemenize yardımcı olabilir ve yalnızca modelin açıklanmasına yardımcı olur, ancak aynı zamanda eğitim işlemine giden gürültülü özelliklerin miktarını azaltmak için bir özellik seçimi yöntemi olarak çıktıyı kullanır.

PFı kullanma hakkında daha fazla bilgi için bkz. [permütasyon özelliği önem derecesi kullanılarak model tahminleri açıklanmıştır](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

## <a name="cross-validation"></a>Çapraz doğrulama

Çapraz doğrulama, verileri birkaç bölüme ayıran ve bu bölümlerde birden çok algoritmaya yönelik bir eğitim ve model değerlendirme tekniğidir. Bu teknik eğitim sürecinde veri tutarak modelin sağlamlığını geliştirir. Veri kısıtlı ortamlarda, görünmeyen gözlemlerdeki performansı iyileştirmeye ek olarak, daha küçük bir veri kümesiyle eğitim modelleri için etkili bir araç olabilir.

[Ml.NET içinde çapraz doğrulamayı nasıl kullanacağınızı](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) öğrenmek için aşağıdaki bağlantıyı ziyaret edin

## <a name="hyperparameter-tuning"></a>Hiper parametre ayarı

Eğitim makinesi öğrenimi modelleri, yinelemeli ve araştırmacı bir işlemdir. Örneğin, K-anlamı algoritmasını kullanarak bir modeli eğitmek için en iyi küme sayısı nedir? Yanıt, verilerin yapısı gibi birçok faktöre bağlıdır. Bu sayının bulunması, k için farklı değerlerle denemeler yapılmasını ve sonra hangi değerin en iyi olduğunu belirleyebilmek için performansı değerlendirmesini gerektirir. En iyi modeli bulmak için bu parametreleri ayarlama yöntemi, Hyper-parametresi ayarlama olarak bilinir.

## <a name="choose-a-different-algorithm"></a>Farklı bir algoritma seçin

Gerileme ve sınıflandırma gibi makine öğrenimi görevleri çeşitli algoritma uygulamaları içerir. Bu sorun, çözmeye çalıştığınız sorunun ve verilerinizin yapısal olarak geçerli algoritmaya uygun olmadığı durumlarda olabilir. Böyle bir durumda, verilerinize daha iyi bilgi edinip öğrenmediğini görmek için göreviniz için farklı bir algoritma kullanmayı göz önünde bulundurun.

Aşağıdaki bağlantı, [hangi algoritmaya seçeceğiniz hakkında](../how-to-choose-an-ml-net-algorithm.md)daha fazla rehberlik sağlar.
