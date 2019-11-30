---
title: Değişiklik kategorilerini bölme-.NET Core
description: .NET Core 'da önemli değişiklikler sınıflandırılan yollar hakkında bilgi edinin.
ms.date: 06/10/2019
ms.openlocfilehash: 4569c1ab19cb9bfa3e16aa8d5f941705eb926fa7
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567921"
---
# <a name="breaking-change-categories"></a>Hataya neden olan değişiklik kategorileri

*Uyumluluk* , kodun ilk olarak geliştirildiği bir .NET uygulaması sürümünde kod derleme veya yürütme imkanını ifade eder. Belirli bir değişiklik, altı farklı şekilde uyumluluğu etkileyebilir. Uyumluluk düşüşü aşağıdaki kategorilere değerlendirirken dikkate alınan [her değişiklik türü](index.md) :

- [davranış değişikliği](#behavioral-change)
- [ikili uyumluluk](#binary-compatibility)
- [Kaynak uyumluluğu](#source-compatibility)
- [Tasarım zamanı uyumluluğu](#design-time-compatibility)
- [geriye dönük uyumluluk](#backwards-compatibility)

[İleri uyumluluk](#forward-compatibility) .NET Core 'un hedefi değildir.

## <a name="behavioral-change"></a>Davranış değişikliği

Davranış değişikliği, üyenin davranışındaki bir değişikliği temsil eder. Değişiklik dışarıdan görünür olabilir (örneğin, bir yöntem farklı bir özel durum oluşturabilir) veya değiştirilmiş bir uygulamayı temsil edebilir (örneğin, bir dönüş değeri hesaplandığında bir değişiklik, iç yöntem çağrılarının eklenmesi veya kaldırılması veya hatta bir önemli performans iyileştirmesi).

Davranış değişiklikleri dışarıdan görünür olduğunda ve bir türün ortak sözleşmesini değiştirirken, ikili uyumluluğu etkilediklerinden beri değerlendirilmesi kolaydır. Uygulama değişikliklerinin değerlendirilmesi çok daha zordur; değişikliğin doğasına ve API kullanmanın sıklığı ve desenlerine bağlı olarak, bir değişikliğin etkisi önemli olan zararsız ile değişebilir.

## <a name="binary-compatibility"></a>İkili uyumluluk

İkili uyumluluk, API 'nin bir tüketicinin yeniden derleme gerekmeden daha yeni bir sürümde API 'yi kullanma becerisini ifade eder. Bu tür değişiklikler ekleme veya bir türe yeni arabirim uygulama ekleme gibi değişiklikler ikili uyumluluğu etkilemez. Bununla birlikte, bir derlemenin ortak imzalarını kaldırmak veya değiştirmek, tüketicilerin derleme tarafından sunulan aynı arabirime artık erişememesi için ikili uyumluluğu etkiler. Bu türden bir değişiklik, *ikili uyumsuz bir değişikliğe göre değişiklik*görmez.

## <a name="source-compatibility"></a>Kaynak uyumluluğu

Kaynak uyumluluğu, bir API 'nin mevcut tüketicilerinin hiçbir kaynak değişiklik yapmadan daha yeni bir sürüme göre yeniden derlenme yeteneğini ifade eder. Bir tüketicinin bir API 'nin daha yeni bir sürümünde başarıyla derlenmesi için kaynak kodu değiştirmesi gerektiğinde, *kaynak uyumsuz bir değişiklik* oluşur.

## <a name="design-time-compatibility"></a>Tasarım zamanı uyumluluğu

Tasarım zamanı uyumluluğu, Visual Studio ve diğer tasarım zamanı ortamlarının sürümleri arasında tasarım zamanı deneyimini korumayı ifade eder. Bu durum, tasarımcı veya tasarımcı kullanıcı arabirimini içerebilir, ancak tasarım zamanı uyumluluğuna ilişkin en önemli boyut, proje uyumluluğuna aittir. Proje veya çözüm açılayabilmelidir ve tasarım zamanı ortamının daha yeni bir sürümünde kullanılabilir.

## <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Geriye dönük uyumluluk, bir API 'nin mevcut bir tüketicisinin aynı şekilde davranırken yeni bir sürüme karşı çalışmasına karşılık gelmektedir. Hem davranış değişiklikleri hem de ikili uyumlulukta yapılan değişiklikler geriye dönük uyumluluğu etkiler. Bir tüketici, API 'nin daha yeni bir sürümüne karşı çalışırken farklı şekilde çalışmayabilir veya davranmayabilir, API geri *uyumsuzdur*.

Geliştiricilerin varsayılan olarak bir API 'nin daha yeni sürümlerinde geriye dönük uyumluluğu beklediği için geriye dönük uyumluluğu etkileyen değişiklikler kesinlikle önerilmez.

## <a name="forward-compatibility"></a>İleriye dönük uyumluluk

İleriye dönük uyumluluk, bir API 'nin mevcut bir tüketicisinin aynı davranışı sergileyen eski bir sürüme karşı çalışmasına karşılık gelmektedir. Bir tüketici, API 'nin eski bir sürümüne karşı çalıştırıldığında farklı bir şekilde çalıştırılamaz veya davranmayabilir, API *İleri doğru uyumsuzdur*.

İleri uyumluluğun sürdürülmesi, daha sonraki bir sürümün daha önceki bir sürümü altında çalışmasını engelleyen bir tüketiciyi engellediği için, sürümden sürümden herhangi bir değişikliği veya eklemeleri neredeyse önler. Geliştiriciler, daha yeni bir API 'yi temel alan bir tüketicinin eski API 'ye karşı düzgün şekilde çalışmayabilir.

İleri uyumluluğun sürdürülmesi .NET Core 'un hedefi değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 'daki kırılmaya karşı değişiklikleri değerlendir](index.md)
