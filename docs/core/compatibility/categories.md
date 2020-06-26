---
title: Uyumluluk
description: .NET 'teki kod değişikliklerinin uyumluluğu etkileyebilecek yollar hakkında bilgi edinin.
ms.date: 06/10/2019
ms.openlocfilehash: 1cf14b7ff4143367653bd1c305cc1dda6711f980
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415699"
---
# <a name="how-code-changes-can-affect-compatibility"></a>Kod değişikliklerinin uyumluluğu nasıl etkileyebileceğinden

*Uyumluluk* , kodun ilk olarak geliştirildiği bir .NET uygulaması sürümünde kod derleme veya yürütme imkanını ifade eder. [Belirli bir değişiklik](index.md) , altı farklı şekilde uyumluluğu etkileyebilir:

- [Davranış değişikliği](#behavioral-change)
- [İkili uyumluluk](#binary-compatibility)
- [Kaynak uyumluluğu](#source-compatibility)
- [Tasarım zamanı uyumluluğu](#design-time-compatibility)
- [Geriye dönük uyumluluk](#backwards-compatibility)
- [Ileriye dönük uyumluluk](#forward-compatibility) (.NET Core 'un hedefi değil)

## <a name="behavioral-change"></a>Davranış değişikliği

Davranış değişikliği, üyenin davranışındaki bir değişikliği temsil eder. Değişiklik dışarıdan görünür olabilir (örneğin, bir yöntem farklı bir özel durum oluşturabilir) veya değiştirilmiş bir uygulamayı temsil edebilir (örneğin, bir dönüş değeri hesaplandığında bir değişiklik, iç yöntem çağrısı veya kaldırma, hatta önemli bir performans geliştirmesi).

Davranış değişiklikleri dışarıdan görünür olduğunda ve bir türün ortak sözleşmesini değiştirirken, ikili uyumluluğu etkilediklerinden beri değerlendirilmesi kolaydır. Uygulama değişikliklerinin değerlendirilmesi çok daha zordur; değişikliğin doğasına ve API kullanmanın sıklığı ve desenlerine bağlı olarak, bir değişikliğin etkisi önemli olan zararsız ile değişebilir.

## <a name="binary-compatibility"></a>İkili uyumluluk

İkili uyumluluk, API 'nin bir tüketicinin yeniden derleme gerekmeden daha yeni bir sürümde API 'yi kullanma becerisini ifade eder. Bu tür değişiklikler ekleme veya bir türe yeni arabirim uygulama ekleme gibi değişiklikler ikili uyumluluğu etkilemez. Bununla birlikte, bir derlemenin ortak imzalarını kaldırmak veya değiştirmek, tüketicilerin derleme tarafından sunulan aynı arabirime artık erişememesi için ikili uyumluluğu etkiler. Bu türden bir değişiklik, *ikili uyumsuz bir değişikliğe göre değişiklik*görmez.

## <a name="source-compatibility"></a>Kaynak uyumluluğu

Kaynak uyumluluğu, bir API 'nin mevcut tüketicilerinin hiçbir kaynak değişiklik yapmadan daha yeni bir sürüme göre yeniden derlenme yeteneğini ifade eder. Bir tüketicinin bir API 'nin daha yeni bir sürümünde başarıyla derlenmesi için kaynak kodu değiştirmesi gerektiğinde, *kaynak uyumsuz bir değişiklik* oluşur.

## <a name="design-time-compatibility"></a>Tasarım zamanı uyumluluğu

Tasarım zamanı uyumluluğu, Visual Studio ve diğer tasarım zamanı ortamlarının sürümleri arasında tasarım zamanı deneyimini korumayı ifade eder. Bu durum, tasarımcı veya tasarımcı kullanıcı arabirimini içerebilir, ancak tasarım zamanı uyumluluğuna ilişkin en önemli boyut, proje uyumluluğuna aittir. Proje veya çözüm açılayabilmelidir ve tasarım zamanı ortamının daha yeni bir sürümünde kullanılabilir.

## <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Geriye dönük uyumluluk, bir API 'nin mevcut bir tüketicisinin aynı şekilde davranırken yeni bir sürüme karşı çalışmasına karşılık gelmektedir. Hem davranış değişiklikleri hem de ikili uyumlulukta yapılan değişiklikler geriye dönük uyumluluğu etkiler. Bir tüketici, API 'nin daha yeni bir sürümüne karşı çalışırken farklı şekilde çalışmayabilir veya davranmayabilir, API geri *uyumsuzdur*.

Geliştiriciler bir API 'nin daha yeni sürümlerinde geriye dönük uyumluluğu beklediği için geriye dönük uyumluluğu etkileyen değişiklikler önerilmez.

## <a name="forward-compatibility"></a>İleriye dönük uyumluluk

İleriye dönük uyumluluk, bir API 'nin mevcut bir tüketicisinin aynı davranışı sergileyen eski bir sürüme karşı çalışmasına karşılık gelmektedir. Bir tüketici, API 'nin eski bir sürümüne karşı çalıştırıldığında farklı bir şekilde çalıştırılamaz veya davranmayabilir, API *İleri doğru uyumsuzdur*.

İleri uyumluluğun sürdürülmesi, daha sonraki bir sürümün daha önceki bir sürümü altında çalışmasını engelleyen bir tüketiciyi engellediği için, sürümden sürümden herhangi bir değişikliği veya eklemeleri neredeyse önler. Geliştiriciler, daha yeni bir API 'yi temel alan bir tüketicinin eski API 'ye karşı düzgün şekilde çalışmayabilir.

İleri uyumluluğun sürdürülmesi .NET Core 'un hedefi değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 'daki kırılmaya karşı değişiklikleri değerlendir](index.md)
