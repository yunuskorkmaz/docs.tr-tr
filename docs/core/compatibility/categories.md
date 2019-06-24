---
title: Yeni değişiklik kategoriler - .NET Core
description: Bozucu değişiklikleri de .NET Core ayrılır yolları hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: 68cd3580e80305e54b41610f05d939a6aff8b54d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307498"
---
# <a name="breaking-change-categories"></a>Yeni değişiklik kategorileri

*Uyumluluk* derleme veya bir .NET uygulaması ile kod ilk olarak geliştirilen textyle farklı bir sürümü üzerinde kod yürütme yeteneği anlamına gelir. Belirli bir değişiklik uyumluluk altı farklı şekilde etkileyebilir. [Tek tek tür uyumluluk değerlendirilirken dikkate alınan değişiklikler](index.md) ilk beş kategoriye ayrılır. 

## <a name="behavioral-change"></a>Davranış değişikliği

Davranış değişikliği üye davranışını bir değişikliği temsil eder. Değişiklik dışarıdan görünür olabilir (örneğin, bir yöntem farklı bir özel durumu atabilir), veya değiştirilmiş bir uygulamasını temsil edebilir (örneğin, bir dönüş değeri hesaplanan şekilde bir değişiklik, eklenmesi veya kaldırılması iç yöntem çağrılarının ve hatta bir önemli bir performans geliştirmesi için).

Davranış değişiklikleri dışarıdan görünen bir türün ortak sözleşme değiştirmek, bunlar ikili uyumluluğu etkiledikleri beri değerlendirmek kolaydır. Uygulama değişiklikleri değerlendirmek çok daha zordur; değişiklik ve sıklığı doğasını ve API'nin kullanım desenleri bağlı olarak, bir değişikliğin etkisini önemli zararsız için değişebilir.  

## <a name="binary-compatibility"></a>İkili uyumluluğu

İkili uyumluluğu, daha yeni sürümünü gerekmeksizin API kullanma yeteneğini API tüketicisinin ifade eder. Bu tür değişiklikleri yöntemler ekleme veya yeni bir arabirim uygulaması için bir tür ekleme olarak ikili uyumluluğu etkilemez. Ancak, kaldırma veya tüketiciler derlemesi tarafından sunulan aynı arabirimi artık erişebilmesi için bir derlemenin ortak imzalarını değiştirmeyi ikili uyumluluğu etkilemez. Bu tür bir değişiklik olarak adlandırılır bir *ikili uyumsuz değişiklik*.

## <a name="source-compatibility"></a>Kaynak uyumluluğu

 Kaynak uyumluluk kaynak değişiklik yapmadan yeni bir sürüme karşı derlemeniz özelliği bir API'nin mevcut tüketici ifade eder. A *kaynağı uyumsuz değişiklik* başarıyla daha yeni bir API sürümüne karşı derleme için kaynak kodunu değiştirmek bir tüketici ihtiyacı olduğunda gerçekleşir.

## <a name="design-time-compatibility"></a>Tasarım zamanı uyumluluğu

Tasarım zamanı deneyimi Visual Studio ve diğer tasarım zamanı ortamları sürümleri arasında koruma için tasarım zaman uyumluluğunu gösterir. Bu davranış veya kullanıcı Arabirimi tasarımcıları, içerebilir, ancak proje uygunluğu tasarım zaman uyumluluğunu en önemli yönüyle ilgilidir. Bir proje veya çözüm açılabilir ve tasarım zamanı ortamında daha yeni bir sürümü üzerinde kullanılan mümkün olması gerekir.

## <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Geriye dönük uyumluluk aynı şekilde davrandığını sırasında yeni bir sürüme karşı çalıştırma olanağı bir API'nin var olan bir tüketici ifade eder. Davranış değişiklikleri hem ikili uyumluluğu değişiklikler geriye dönük uyumluluk etkiler. Bir tüketici çalıştırabilir veya daha yeni API sürümüne karşı çalışan farklı davranır değilse API'dir *geriye dönük uyumlu*.

Varsayılan olarak geliştiriciler, geriye doğru uyumluluk yeni API sürümlerinde beklediğiniz olduğundan, geriye dönük uyumluluk etkileyen değişiklikler kesinlikle önerilmez.

## <a name="forward-compatibility"></a>İleriye dönük uyumluluk

İleriye dönük bir API'nin var olan bir tüketicinin aynı davranış sergileyen hatayla karşı daha eski bir sürümünü çalıştırma olanağı ifade eder. Bir tüketici çalıştırmak mümkün değilse veya farklı daha eski bir API sürümünü karşı çalıştırdığınızda, API'dir davranışını *iletme uyumsuz*. 

Önceki bir sürümü altında çalışmasını sonraki bir sürümünü hedefleyen bir tüketici bu değişiklikleri önlemek beri neredeyse ileriye dönük bakım herhangi bir değişiklik veya eklemeler sürümden sürüme ışığının. Geliştiriciler, daha yeni bir API'yi kullanır bir tüketici karşı eski API düzgün çalışmayabilir bekler. 

İleriye dönük bakım, .NET Core hedefi değil.

## <a name="see-also"></a>Ayrıca bkz.

[.NET core'da bozucu değişiklikleri değerlendir](index.md)
