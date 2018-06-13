---
title: .NET sınıf kitaplıkları
description: Nasıl .NET sınıf kitaplıkları, Grup yararlı işlevi için birden çok uygulama tarafından kullanılan modüllere etkinleştirmek öğrenin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: 7d2f81ef08892c994163d609a56008c1accadaa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570617"
---
# <a name="net-class-libraries"></a>.NET sınıf kitaplıkları

Sınıf kitaplıkları olan [paylaşılan kitaplık](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) .NET kavramı. Birden çok uygulama tarafından kullanılan modüllere kullanışlı işlevsellik componentize olanak sağlar. Gerekli veya uygulama başlangıcında bilinmiyor işlevselliği yüklenirken olarak de kullanılabilir. Sınıf kitaplıkları kullanarak açıklanmıştır [.NET derleme dosyası biçimi](assembly-format.md).

Kullanabileceğiniz sınıf kitaplıkları üç tür vardır:

*   **Platforma özgü** sınıf kitaplıkları tüm API'leri (örneğin, .NET Framework, Xamarin iOS için) belirli bir platformda erişimi, ancak yalnızca uygulamaları ve bu platformu hedefleyen kitaplıklar tarafından kullanılabilir.
*   **Taşınabilir** sınıf kitaplıkları API kümesini erişimi ve uygulamaları ve birden çok platformu hedefleyen kitaplıklar tarafından kullanılabilir.
*   **.NET standart** sınıf kitaplıkları olan bir birleşme hem de en iyi sağlayan tek bir modelini platforma özgü ve taşınabilir kitaplığı prototip.

## <a name="platform-specific-class-libraries"></a>Platforma özgü sınıf kitaplıkları

Platforma özgü kitaplıkları tek bir .NET uygulaması (örneğin, Windows .NET Framework) bağlı olan ve bu nedenle önemli bağımlılıkları bilinen yürütme ortamda alabilir. Bu tür bir ortamda bilinen bir dizi API (.NET ve işletim sistemi API'leri) kullanıma sunmak ve korumak ve beklenen durumu (örneğin, Windows kayıt defteri) kullanıma sunar.

Platform belirli kitaplıkları oluşturan geliştiriciler, temel platform olarak tam olarak yararlanabilir. Kitaplıkların her zaman sadece platform denetimleri veya başka biçimlerde koşullu kod (modül birden çok platform için tek kaynak belirleme kodu) gereksiz yapmadan platform, verilen çalışır.

Platforma özgü kitaplıkları, .NET Framework için birincil sınıf kitaplığı türü olmuştur. Diğer .NET uygulamaları ortaya çıktı gibi platforma özgü kitaplıkları baskın kitaplık türünü kalan.

## <a name="portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları

Taşınabilir kitaplıklara birden çok .NET uygulamalarında desteklenir. Bunlar yine bir bilinen yürütme ortamı bağımlılıkları alabilir, ancak, bir dizi somut .NET uygulamalarında kesişimi ile oluşturulan bir yapay ortamıdır. Bu açık API'ler ve platform varsayımlar ne platforma özgü kitaplığa kullanılabilir olacağını, bir alt anlamına gelir.

Taşınabilir bir kitaplık oluşturduğunuzda bir platform yapılandırması seçin. Bu, (örneğin, .NET Framework 4.5 +, Windows Phone 8.0 +) desteklemesi gereken platformlar kümesidir. Destek, daha az API'leri ve daha az platform varsayımlar opt daha fazla platformlar yapabilirsiniz, en düşük genel payda. Bu özellik ilk başta, kişiler bu yana genellikle düşünme "daha, daha fazla platformlar sonuçlar daha az kullanılabilir API'leri desteklenen Bul ancak iyidir" kafa karıştırıcı olması.

Birçok kitaplığı geliştiricileri birden çok platforma özgü kitaplıklarını (koşullu derleme yönergeleri kullanarak) bir kaynaktan oluşturan taşınabilir kitaplıklara geçtiniz. Vardır [çeşitli yaklaşımlar](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) taşınabilir kitaplıklara içinde platforma özgü işlevselliği erişmek için [yemi anahtar](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) en yaygın olan kabul teknik bu noktada.

### <a name="net-standard-class-libraries"></a>.NET standart sınıf kitaplıkları

.NET standart kitaplıkları yerine yeni bir platforma özgü ve taşınabilir kitaplıkları kavramlarını ' dir. Platforma özgü (yapay platformları veya platform kesişimlerini) temel platformdan tüm işlevselliği kullanıma herkese açık. Bunlar, tüm desteklenen platformlarda çalıştıkları herkese açık taşınabilir.

.NET standart kitaplığı kümesi sunan _sözleşmeleri_. .NET uygulamaları, tam olarak ya da hiç her sözleşme desteklemesi gerekir. Her uygulama, bu nedenle, .NET Standart sözleşmeler, bir kümesini destekler. Corollary olan kullanıcının sözleşme bağımlılıkları .NET standart her sınıf kitaplığı destekleyen platformlarda desteklenir.

.NET standart .NET Framework'ün tüm işlevselliği kullanıma sunmuyor (ya da bir hedefi olan), ancak bunlar taşınabilir sınıf kitaplıkları daha pek çok daha fazla API'lerini kullanıma. Daha fazla API'leri zamanla eklenir.

.NET standart kitaplıkları aşağıdaki platformları destekler:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Evrensel Windows Platformu (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Daha fazla bilgi için bkz: [.NET standart](net-standard.md) konu.

### <a name="mono-class-libraries"></a>Mono sınıf kitaplıkları

Sınıf kitaplıkları Mono kitaplıkları yukarıda açıklanan üç tür dahil olmak üzere üzerinde desteklenir. Mono genellikle (doğru) olarak Microsoft .NET Framework'ün bir platformlar arası uygulaması görüldü. Kısmen platforma özgü .NET Framework kitaplıkları Mono çalışma zamanı değiştirilme ya da yeniden derleme olmadan çalışan çünkü bu oluştu. Bu özellik taşınabilir sınıf kitaplıkları oluşturulmasını önce yerinde olduğu şekilde (yalnızca tek yönlü çalıştınız rağmen) .NET Framework ve Mono arasında ikili taşınabilirlik etkinleştirmek için belirgin bir seçim oluştu.
