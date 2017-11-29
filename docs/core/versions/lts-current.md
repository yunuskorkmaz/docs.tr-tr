---
title: ".NET Core Desteği"
description: ".NET Core için farklı bir sürüm tren destekler (LTS ve geçerli) hakkında bilgi edinin"
keywords: ".NET, .NET core, lts, geçerli, ft, destek, destek trenler izler, yaşam döngüsü, yayın trenler destekler"
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
ms.openlocfilehash: 254611ef05af22eea616fcfe3288239a744e0ccc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-support"></a>.NET Core Desteği

.NET Core Destek genel bir açıklamasını budur.

## <a name="lts-and-current-release-trains"></a>LTS ve geçerli sürüm trenler

İki destek yayın trenler sahip, .NET Core gibi açık kaynaklı projeleri için özel yazılım dünyanın her kullanımda ortak bir kavramıdır. .NET core trenler yayın aşağıdaki desteği vardır: [uzun süreli destek (LTS)](https://en.wikipedia.org/wiki/Long-term_support) ve geçerli. LTS yayımları için kararlılık önemli sorunlar için ve güvenlik düzeltmeleri alma yaşam döngüleri saklanır. Yeni özellik çalışma ve ek hata düzeltmeleri geçerli sürümlerde gerçekleşir. Destek açısından bakıldığında, bu sürüm trenler yaşam döngüsü öznitelikleri desteği aşağıdaki vardır.

LTS sürümlerdir
* Üç yıl sonra genel kullanılabilirlik tarihine LTS sürümü için desteklenen
* Veya bir yıl sonra bir sonraki LTS yayın genel kullanılabilirliği

Geçerli sürümlerdir
* Yayın LTS olarak aynı üç yıla penceresi içinde desteklenen
* Desteklenen bir sonraki geçerli sürümünün genel kullanılabilirlik sonra üç ay için
* Ve bir yıl sonra bir sonraki LTS yayın genel kullanılabilirliği

## <a name="versioning"></a>Sürüm oluşturma
Yeni LTS sürümler ana sürüm numarasını artış işaretlenir. Karşılık gelen LTS tren aynı ana numarasına sahip ve ikincil sürüm numarası artış tarafından işaretlenen geçerli serbest bırakır. Örneğin, 1.0.3 LTS olacaktır ve 1.1.0 geçerli olacaktır. Hata düzeltmesi ya da tren artışı düzeltme sürümüne güncelleştirir. Sürüm oluşturma şeması hakkında daha fazla bilgi için bkz: [.NET Core sürüm](index.md).

## <a name="what-causes-updates-in-lts-and-current-trains"></a>Güncelleştirmeleri LTS ve geçerli trenler nedeni nedir?
Sayı güncelleştirmeleri sürüme hata düzeltmeleri veya API ' larını eklenmesi gibi belirli hangi değişiklikleri neden anlamak için karar ağacı bölümünde gözden geçirin [sürüm belgeleri](index.md). Geçerli LTS daldan içine hangi değişiklikleri çekilen karar kuralları altın kümesi değil. Genellikle, gerekli güvenlik güncelleştirmeleri ve beklenen davranışa düzeltme düzeltme ekleri LTS şube güncelleştirmek için nedenleri açıklanmaktadır. Bu her zaman mümkün olmayabilir ancak biz de LTS dalda son Masaüstü Geliştirici işletim sistemleri desteklemek istiyorsanız. Göz atmak için belirli bir sürümde desteklenen hangi API'leri, düzeltmeler ve işletim sistemleri üzerinde Yakala en iyi yolu olan kendi [sürüm notları](https://github.com/dotnet/core/tree/master/release-notes) github'da.

### <a name="further-reading"></a>Daha Fazla Bilgi
* [.NET core destek yaşam döngüsü olgu sayfası](https://www.microsoft.com/net/core/support)
* [Şu anda desteklenen işletim sistemleri ve sürümleri](https://github.com/dotnet/core/blob/master/roadmap.md)
