---
title: .NET sınıf kitaplıkları
description: .NET sınıf kitaplıkları, nasıl Grup yararlı işlevleri için birden çok uygulama tarafından kullanılan modüller halinde olanak öğrenin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: d5b067f299d96b687d44b83e431d89667f2d84f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772651"
---
# <a name="net-class-libraries"></a>.NET sınıf kitaplıkları

Sınıf kitaplıklarının [paylaşılan kitaplık](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) .NET kavramı. Birden çok uygulama tarafından kullanılan modüller halinde kullanışlı işlevsellik componentize sağlıyor. Gerekli olmadığında veya uygulama başlatılırken bilinmeyen işlevselliği yükleme olarak de kullanılabilir. Sınıf kitaplıkları kullanılarak tanımlanır [.NET bütünleştirilmiş kodu dosya biçimi](assembly/file-format.md).

Kullanabileceğiniz sınıf kitaplıkları üç tür vardır:

* **Platforma özgü** sınıf kitaplıkları, tüm API'lere erişim (örneğin, .NET Framework, Xamarin iOS için) belirli bir platforma sahip, ancak yalnızca uygulamaları ve bu platformu hedefleyen kitaplıklar tarafından kullanılabilir.
* **Taşınabilir** sınıf kitaplıkları API kümesini erişimi ve uygulamaları ve birden çok platformu hedefleyen kitaplıklar tarafından kullanılabilir.
* **.NET standard** sınıf kitaplıkları vardır ve her ikisinin sağlayan bir tek modeline platforma özgü ve taşınabilir kitaplık kanıtı birleşmesi.

## <a name="platform-specific-class-libraries"></a>Platforma özgü sınıf kitaplıkları

Platforma özgü kitaplıklar tek bir .NET uygulaması (örneğin, Windows üzerinde .NET Framework) bağlıdır ve önemli bağımlılıkları bir bilinen yürütme ortamında bu nedenle alabilir. Böyle bir ortam API'leri (.NET ve işletim sistemi API'leri) bilinen bir dizi kullanıma korumak ve beklenen durumu (örneğin, Windows kayıt defteri) kullanıma sunar.

Platforma özgü kitaplıklar oluşturmak geliştiriciler, temel alınan platformu tam olarak yararlanabilir. Kitaplıkları, her zaman sadece platformu, platform denetimleri veya diğer tür koşullu kodu (mod, birden çok platform için tek kaynağını kod) gereksiz yapma verilen üzerinde çalışır.

Platforma özgü kitaplıklar, .NET Framework için birincil sınıf kitaplığı türü silinmiş. Diğer .NET uygulamaları ortaya gibi platforma özgü kitaplıklar baskın kitaplık türünü kaldı.

## <a name="portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları

Taşınabilir kitaplıklar, birden çok .NET uygulamalarında desteklenir. Bunlar yine de bir bilinen yürütme ortamında bağımlılıkları alabilir, ancak bir dizi somut .NET uygulamalarını kesişimi ile oluşturulan yapay bir ortamdır. Bu açık API'ler ve platform varsayımlar ne bir platforma özgü kitaplığında kullanılabilir hale gelir, bir alt anlamına gelir.

Taşınabilir Kitaplığı oluştururken bir platform yapılandırmasını seçin. Bunlar için (örneğin, .NET Framework 4.5 +, Windows Phone 8.0 +) desteklemek için gereken platformları yer alır. Daha fazla platform desteği, daha az API'leri ve yapabileceğiniz, daha az sayıda platform varsayımlar en küçük ortak paydası iyileştirilmiş. Bu özelliğin ilk başta, kişilerin bu yana genellikle düşünme "daha, daha fazla platformlar sonuçları daha az kullanılabilir API'leri desteklenen Bul ancak daha iyidir" kafa karıştırıcı olması.

Geliştiricilerin çoğu kitaplık üretir birden çok platforma özgü kitaplıklar (koşullu derleme yönergeleri kullanarak) bir kaynaktan gelen, taşınabilir kitaplıklara geçtiniz. Vardır [çeşitli yaklaşımlar](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) taşınabilir kitaplıklar, platforma özgü işlevinin erişmek için [baıt anahtar](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) en yaygın olan kabul yöntemi bu noktada.

## <a name="net-standard-class-libraries"></a>.NET standart sınıf kitaplıkları

.NET standard kitaplıkları yenisini platforma özgü ve taşınabilir kitaplıklar kavramları vardır. Platforma özgü oldukları anlamında bunlar temel alınan Platformu (yapay platformları veya platform kesişimlerini) tüm işlevselliği kullanıma sunma. Bunlar tüm destekleyici platformlar üzerinde çalıştıkları anlamında taşınabilir.

.NET Standard kitaplığı kümesi sunan _sözleşmeleri_. .NET uygulamaları, tam olarak ya da hiç her sözleşme desteklemesi gerekir. Her uygulama, bu nedenle, .NET Standard sözleşmeleri kümesini destekler. Corollary her .NET Standard sınıf kitaplığı, sözleşme bağımlılıklarını destekleyen platformlarında desteklenir.

.NET standart .NET Framework'ün tamamını işlevselliğini kullanıma sunmuyor (ya da bir hedefi olan), ancak bunlar taşınabilir sınıf kitaplıkları daha pek çok daha fazla API'leri kullanıma. Zaman içinde daha fazla API eklenir.

.NET Standard kitaplıkları aşağıdaki platformları destekler:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Evrensel Windows Platformu (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Daha fazla bilgi için [.NET Standard](net-standard.md) konu.

## <a name="mono-class-libraries"></a>Mono sınıf kitaplıkları

Sınıf kitaplıkları kitaplıkları yukarıda açıklanan üç türü de dahil olmak üzere, Mono desteklenir. Mono genellikle (doğru) Microsoft .NET Framework'ün bir platformlar arası uygulama görüldü. Platforma özgü .NET Framework kitaplıkları değişiklik olmadan veya yeniden derleme Mono çalışma zamanı üzerinde çalıştırabileceğiniz parçası olarak, bu nedeni. Bu özellik taşınabilir sınıf kitaplıkları oluşturma önce bir yerde olduğu şekilde (sadece tek yöndedir eşleştirmenin rağmen) .NET Framework ve Mono arasında ikili taşınabilirlik etkinleştirmek için bir belirgin seçim oluştu.
