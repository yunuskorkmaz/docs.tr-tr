---
title: .NET sınıf kitaplıkları
description: .NET sınıf kitaplıklarının, birden çok uygulama tarafından kullanılabilecek modüller için yararlı işlevler gruplandırılmasına nasıl olanak sağladığını öğrenin.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: e2fd0237556f877af64708674f00e9efddf95869
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209649"
---
# <a name="net-class-libraries"></a>.NET sınıf kitaplıkları

Sınıf kitaplıkları, .NET için [Paylaşılan kitaplık](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) kavramıdır. Bu kişiler, birden çok uygulama tarafından kullanılabilen modüller için yararlı işlevsellik oluşturmanız olanaklı hale gelir. Bunlar ayrıca, gerekli olmayan veya uygulama başlangıcında bilinmeyen bir işlevi yükleme yöntemi olarak da kullanılabilir. Sınıf kitaplıkları [.NET derleme dosyası biçimi](assembly/file-format.md)kullanılarak açıklanır.

Kullanabileceğiniz üç tür sınıf kitaplığı vardır:

* **Platforma özgü** sınıf kitaplıkları, belirli bir platformdaki tüm API 'lere erişebilir (örneğin, .NET Framework, Xamarin iOS), ancak yalnızca söz konusu platformu hedefleyen uygulamalar ve kitaplıklar tarafından kullanılabilir.
* **Taşınabilir** sınıf kitaplıklarının bir API alt kümesine erişimi vardır ve birden çok platformu hedefleyen uygulamalar ve kitaplıklar tarafından kullanılabilir.
* **.NET Standard** sınıf kitaplıkları, platforma özgü ve taşınabilir kitaplık kavramının her ikisinin de en iyi şekilde sağladığı tek bir modele birleşmesi.

## <a name="platform-specific-class-libraries"></a>Platforma özgü sınıf kitaplıkları

Platforma özgü kitaplıklar tek bir .NET uygulamasına bağlıdır (örneğin, Windows üzerinde .NET Framework) ve bu nedenle bilinen bir yürütme ortamında önemli bağımlılıklar gerçekleştirebilir. Böyle bir ortam, bilinen bir API kümesini (.NET ve işletim sistemi API 'Leri) kullanıma sunar ve beklenen durumu (örneğin, Windows kayıt defteri) korur ve kullanıma sunar.

Platforma özgü kitaplıklar oluşturan geliştiriciler, temel alınan platformun tamamen yararlanabilir. Kitaplıklar yalnızca söz konusu platformda çalışır, platform denetimleri veya diğer koşullu kod formları gereksizdir (modül birden çok platform için tek kaynak kodu oluşturma).

Platforma özgü kitaplıklar .NET Framework için birincil sınıf kitaplığı türüdür. Diğer .NET uygulamaları ortaya çıktı olsa da, platforma özgü kitaplıklar, baskın kitaplık türünü de kapatmalıdır.

## <a name="portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları

Taşınabilir kitaplıklar çoklu .NET uygulamalarında desteklenir. Ancak, bilinen bir yürütme ortamında bağımlılıklar alabilir, ancak ortam, somut bir .NET uygulaması kümesinin kesişimi tarafından oluşturulan yapay bir değer olabilir. Sunulan API 'Ler ve platform varsayımları, platforma özgü bir kitaplıkta kullanılabilecek bir alt kümesidir.

Taşınabilir bir kitaplık oluştururken bir platform yapılandırması seçersiniz. Platform yapılandırması, desteklemeniz gereken platformlar kümesidir (örneğin, .NET Framework 4.5 +, Windows Phone 8.0 +). Desteklemeyi tercih ettiğiniz daha fazla platform, daha az sayıda API ve daha az platform varsayımları, en düşük ortak paydası. Bu özellik ilk olarak "daha fazla" daha iyi olduğunu düşündükleri, ancak daha Desteklenen platformların daha az kullanılabilir API 'Lerle sonuçlandığından emin olmak için kafa karıştırıcı olabilir.

Birçok kitaplık geliştiricisi, bir kaynaktan (koşullu derleme yönergeleri kullanılarak) birden çok platforma özgü kitaplık oluşturmaktan taşınabilir kitaplıklara geçiş yaptı. Taşınabilir kitaplıklar içindeki platforma özgü işlevlere erişmek için, Bait-ve-bu noktada en yaygın olarak kabul edilen teknikle geçiş yapmak için [birkaç yaklaşım](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) vardır.

## <a name="net-standard-class-libraries"></a>.NET Standard sınıf kitaplıkları

.NET Standard kitaplıklar, platforma özgü ve taşınabilir kitaplıklar kavramlarının yerini alır. Temel platformdaki tüm işlevleri kullanıma sundukları (yapay platform veya platform kesişimleri olmadan), platforma özgüdür. Tüm destekleyici platformlarda çalıştıkları anlamda taşınabilir.

.NET Standard bir kitaplık _sözleşmeleri_kümesi sunar. .NET uygulamalarının her sözleşmeyi tamamen desteklemesi veya hiç olmaması gerekir. Bu nedenle, her uygulama, bir .NET Standard sözleşmeleri kümesini destekler. Bu, her bir .NET Standard sınıf kitaplığının, anlaşma bağımlılıklarını destekleyen platformlarda desteklenmesine bağlıdır.

.NET Standard, .NET Framework işlevselliğinin tamamını açığa çıkarır (veya bir hedef değildir), ancak taşınabilir sınıf kitaplıklarından birçok API 'yi kullanıma sunırlar. Zamana göre daha fazla API eklenecektir.

Aşağıdaki platformlar .NET Standard kitaplıklarını destekler:

* .NET Core
* .NET Framework
* Mono
* Xamarin. iOS, Xamarin. Mac, Xamarin. Android
* Evrensel Windows Platformu (UWP)
* Windows
* Windows Phone
* Windows Phone Silverlight

Daha fazla bilgi için bkz. [.NET Standard](net-standard.md).

## <a name="mono-class-libraries"></a>Mono sınıfı kitaplıkları

Sınıf kitaplıkları, daha önce açıklanan üç kitaplık türü de dahil olmak üzere mono 'da desteklenir. Mono genellikle .NET Framework platformlar arası bir uygulama olarak görülmüştür (doğru şekilde). Bunun bir parçası olarak, platforma özgü .NET Framework kitaplıklarının, değişiklik veya yeniden derleme olmadan mono çalışma zamanında çalıştırılabilmesi nedeniyle oldu. Bu özellik taşınabilir sınıf kitaplıklarının oluşturulmasından önce vardı, bu nedenle .NET Framework ve mono arasında ikili taşınabilirliği etkinleştirmek için açık bir seçimdir (ancak yalnızca bir yönde çalıştık).
