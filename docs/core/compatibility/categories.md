---
title: Hataya neden olan değişiklik kategorileri
description: .NET Core'da kesme değişikliklerinin nasıl kategorize edildiği hakkında bilgi edinin.
ms.date: 06/10/2019
ms.openlocfilehash: b273ebbb82da803cde66ea34760aa1779c6c1ca5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093051"
---
# <a name="breaking-change-categories"></a>Hataya neden olan değişiklik kategorileri

*Uyumluluk,* kodun ilk geliştirildiği uygulama dışında bir .NET uygulamasının sürümünde kod derleme veya yürütme olanağı anlamına gelir. Belirli bir değişiklik altı farklı şekilde uyumluluğu etkileyebilir. Uyumluluğu değerlendirirken göz önünde bulundurulan [tek tek değişiklik türleri](index.md) aşağıdaki kategorilere girer:

- [davranış değişikliği](#behavioral-change)
- [ikili uyumluluk](#binary-compatibility)
- [kaynak uyumluluğu](#source-compatibility)
- [tasarım-zaman uyumluluğu](#design-time-compatibility)
- [geriye dönük uyumluluk](#backwards-compatibility)
- [ileri uyumluluk](#forward-compatibility) (.NET Core hedefi değil)

## <a name="behavioral-change"></a>Davranış değişikliği

Davranış değişikliği, bir üyenin davranışındaki değişikliği temsil eder. Değişiklik dışarıdan görülebilir (örneğin, bir yöntem farklı bir özel durum açabilir) veya değiştirilmiş bir uygulamayı temsil edebilir (örneğin, iade değerinin hesaplanma şeklindeki bir değişiklik, dahili yöntem çağrılarının eklenmesi veya kaldırılması, hatta önemli performans artışı).

Davranış değişiklikleri dışarıdan görünür olduğunda ve bir türün ortak sözleşmesini değiştirdiğinde, ikili uyumluluğu etkilediği için değerlendirilmesi kolaydır. Uygulama değişikliklerini değerlendirmek çok daha zordur; değişikliğin doğasına ve API'nin kullanım sıklığına ve şekillerine bağlı olarak, bir değişikliğin etkisi şiddetliden zararsıza kadar değişebilir.

## <a name="binary-compatibility"></a>İkili uyumluluk

İkili uyumluluk, bir API tüketicisinin API'yi yeniden derleme olmadan yeni bir sürümde kullanabilme yeteneğini ifade eder. Yöntem ekleme veya bir türe yeni bir arabirim uygulaması ekleme gibi değişiklikler ikili uyumluluğu etkilemez. Ancak, tüketicilerin derleme tarafından açığa çıkarılan aynı arabirime artık erişebilmeleri için bir derlemenin ortak imzalarını kaldırmak veya değiştirmek ikili uyumluluğu etkiler. Bu tür bir değişiklik *ikili uyumsuz değişiklik*denir.

## <a name="source-compatibility"></a>Kaynak uyumluluğu

Kaynak uyumluluğu, bir API'nin mevcut tüketicilerinin kaynak değişikliği olmadan yeni bir sürüme karşı yeniden derleme yeteneğini ifade eder. Bir *kaynağın uyumsuz bir değişikliği,* bir tüketicinin API'nin daha yeni bir sürümüne karşı başarılı bir şekilde oluşturabilmesi için kaynak kodunu değiştirmesi gerektiğinde oluşur.

## <a name="design-time-compatibility"></a>Tasarım zamanı uyumluluğu

Tasarım zamanı uyumluluğu, Visual Studio ve diğer tasarım zamanı ortamlarının sürümlerinde tasarım zamanı deneyiminin korunması anlamına gelir. Bu davranış veya tasarımcıların UI içerebilir iken, tasarım-zaman uyumluluğu en önemli yönü proje uyumluluğu ile ilgilidir. Bir proje veya çözüm, tasarım zamanı ortamının daha yeni bir sürümünde açılabilir ve kullanılabilmelidir.

## <a name="backwards-compatibility"></a>Geriye dönük uyumluluk

Geriye dönük uyumluluk, bir API'nin varolan bir tüketicisinin aynı şekilde davranarak yeni bir sürüme karşı çalışma yeteneğini ifade eder. Hem davranış değişiklikleri hem de ikili uyumluluktaki değişiklikler geriye dönük uyumluluğu etkiler. Bir tüketici API'nin yeni sürümüne karşı çalışırken farklı şekilde çalıştıramazsa veya farklı davranamazsa, API *geriye doğru uyumsuzdur.*

Geliştiriciler bir API'nin yeni sürümlerinde geriye dönük uyumluluk beklediğinden, geriye dönük uyumluluğu etkileyen değişiklikler önerilmez.

## <a name="forward-compatibility"></a>İleriye dönük uyumluluk

İleriye dönük uyumluluk, bir API'nin varolan bir tüketicisinin aynı davranışı sergilerken eski bir sürüme karşı çalışma yeteneğini ifade eder. Bir tüketici API'nin eski bir sürümüne karşı çalıştırıldığında farklı şekilde çalıştırılamazsa veya farklı davranamazsa, API *ileri uyumsuzdur.*

İleriye dönük uyumluluğu korumak, bu değişiklikler daha sonraki bir sürümün önceki bir sürüm altında çalışmasını hedefleyen bir tüketiciyi engellediğinden, sürümden sürüme herhangi bir değişiklik veya eklemeyi neredeyse engeller. Geliştiriciler, yeni bir API'ye dayanan bir tüketicinin eski API'ye karşı doğru şekilde çalışmamasını bekler.

İleriye uyumluluğu korumak .NET Core'un bir hedefi değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core'daki kırılma değişikliklerini değerlendirme](index.md)
