---
title: .NET sınıf kitaplıkları
description: .NET sınıf kitaplıklarının yararlı işlevleri birden çok uygulama tarafından kullanılabilecek modüllerde gruplandırmanızı nasıl sağladığını öğrenin.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: b7934e5def202760ab05d363ee5fcda5d012ca72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124591"
---
# <a name="net-class-libraries"></a>.NET sınıf kitaplıkları

Sınıf kitaplıkları .NET için [ortak kitaplık](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) kavramıdır. Bunlar, yararlı işlevleri birden çok uygulama tarafından kullanılabilecek modüllere bileşenleştirmenize olanak tanır. Ayrıca, uygulama nın başlatılmasında gerekli olmayan veya bilinmeyen yükleme işlevi olarak da kullanılabilirler. Sınıf kitaplıkları [.NET Assembly dosya biçimi](assembly/file-format.md)kullanılarak açıklanmıştır.

Kullanabileceğiniz üç tür sınıf kitaplığı vardır:

* **Platforma özgü** sınıf kitaplıkları belirli bir platformdaki tüm API'lere erişebilir (örneğin, .NET Framework, Xamarin iOS), ancak yalnızca bu platformu hedefleyen uygulamalar ve kitaplıklar tarafından kullanılabilir.
* **Taşınabilir** sınıf kitaplıkları API'lerin bir alt kümesine erişebilir ve birden çok platformu hedefleyen uygulamalar ve kitaplıklar tarafından kullanılabilir.
* **.NET Standart** sınıf kitaplıkları, platforma özgü ve taşınabilir kitaplık kavramının her ikisini de en iyi şekilde sağlayan tek bir modelle birleşmesidir.

## <a name="platform-specific-class-libraries"></a>Platforma özel sınıf kitaplıkları

Platforma özgü kitaplıklar tek bir .NET uygulamasına bağlıdır (örneğin, .Windows'da .NET Framework) ve bu nedenle bilinen bir yürütme ortamına önemli bağımlılıklar alabilir. Böyle bir ortam bilinen bir API kümesini (.NET ve OS API'leri) ortaya çıkarır ve beklenen durumu (örneğin, Windows kayıt defteri) korur ve ortaya çıkarır.

Platforma özgü kitaplıklar oluşturan geliştiriciler, temel platformu tamamen kullanabilir. Kütüphaneler yalnızca o platformda çalışacak, platform denetimlerini veya diğer koşullu kod biçimlerini gereksiz hale getirecektir (birden çok platform için modüler tek kaynak kodu).

Platforma özgü kitaplıklar .NET Framework için birincil sınıf kitaplığı türü olmuştur. Diğer .NET uygulamaları ortaya çıktığında bile, platforma özgü kütüphaneler baskın kitaplık türü olarak kaldı.

## <a name="portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları

Taşınabilir kitaplıklar birden çok .NET uygulamasında desteklenir. Onlar hala bilinen bir yürütme ortamına bağımlılık alabilir, ancak, çevre beton bir dizi kesiştiği tarafından oluşturulan sentetik bir .NET uygulamaları. Bu, açığa çıkarılan API'lerin ve platform varsayımlarının platforma özgü bir kitaplık için nelerin kullanılabileceğinin bir alt kümesi olduğu anlamına gelir.

Taşınabilir kitaplık oluşturduğunuzda bir platform yapılandırması seçersiniz. Bunlar desteklemeniz gereken platformlar kümesidir (örneğin, .NET Framework 4.5+, Windows Phone 8.0+). Ne kadar çok platformu desteklemeyi seçerseniz, o kadar az API ve daha az platform varsayımı yaparsanız, en düşük ortak payda dır. İnsanlar genellikle "daha iyi" olduğunu düşündüklerinden, ancak daha fazla desteklenen platformun daha az kullanılabilir API'ye neden olduğunu düşündüklerinden, bu özellik ilk başta kafa karıştırıcı olabilir.

Birçok kitaplık geliştiricisi, tek bir kaynaktan birden çok platforma özgü kitaplık (koşullu derleme yönergelerini kullanarak) taşınabilir kitaplıklar için geçiş yaptı. Taşınabilir [kitaplıklarda](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) platforma özgü işlevsellik lere erişmek için çeşitli yaklaşımlar vardır ve bu noktada yem [ve anahtar](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) en yaygın olarak kabul edilen tekniktir.

## <a name="net-standard-class-libraries"></a>.NET Standart sınıf kitaplıkları

.NET Standart kitaplıklar, platforma özgü ve taşınabilir kitaplık kavramlarının yerini alır. Bunlar, temel platformdaki tüm işlevselliği (sentetik platformlar veya platform kesişimleri) ortaya çıkarmaları anlamında platforma özgüdür. Tüm destek platformlarında çalıştıkları anlamında taşınabilirdirler.

.NET Standardı bir dizi kitaplık _sözleşmesi_ni ortaya çıkarır. .NET uygulamaları her sözleşmeyi tam olarak veya hiç desteklememelidir. Bu nedenle, her uygulama bir dizi .NET Standart sözleşmesini destekler. Sonuç olarak, her .NET Standart sınıf kitaplığı sözleşme bağımlılıklarını destekleyen platformlarda desteklenir.

.NET Standardı .NET Framework'ün tüm işlevselliğini (veya bir hedef olduğunu) göstermez, ancak Taşınabilir Sınıf Kitaplıklarından çok daha fazla API açığa çıkarır. Zaman içinde daha fazla API eklenecektir.

Aşağıdaki platformlar .NET Standart kitaplıklarını destekler:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Evrensel Windows Platformu (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Daha fazla bilgi için [.NET Standart](net-standard.md) konusuna bakın.

## <a name="mono-class-libraries"></a>Mono sınıf kitaplıkları

Sınıf kitaplıkları, yukarıda açıklanan üç tür kitaplık da dahil olmak üzere Mono'da desteklenir. Mono, Microsoft .NET Framework'ün platformlar arası bir uygulaması olarak sık sık (doğru) görülmüştür. Bunun nedeni kısmen, platforma özgü .NET Framework kitaplıkları mono çalışma zamanında değişiklik veya yeniden derleme olmadan çalıştırılabiliyordu. Bu özellik taşınabilir sınıf kitaplıkları oluşturulmadan önce yerinde ydi, bu nedenle .NET Framework ve Mono arasında ikili taşınabilirliği etkinleştirmek için bariz bir seçimdi (her ne kadar tek bir yönde işe yaramış olsa da).
