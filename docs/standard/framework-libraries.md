---
title: Framework Kitaplıkları
description: Birçok genel ve uygulamaya özgü türleri, algoritmaları ve yardımcı işlevleri için kitaplıkları uygulamaları nasıl sağladığını öğrenin.
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: 1e825efcb2a352c823391fb0dad3d566189da001
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425533"
---
# <a name="framework-libraries"></a>Framework Kitaplıkları

.NET sınıf kitaplıkları için taban sınıfı kitaplıkları (çekirdek kümesi) veya framework sınıf kitaplıkları (eksiksiz) adlandırılır, inanılmaz bir standart kümesine sahiptir. Bu kitaplıklar birçok genel ve uygulamaya özgü türleri, algoritmaları ve yardımcı işlevleri için uygulamalar sağlar. Bilgi işlem görevlerini geniş bir kümesi için kullanımı kolay kullanıma hazır kitaplıkları sağlama framework sınıf kitaplıkları üzerinde hem ticari hem de topluluk kitaplıklar oluşturun.

Bu kitaplıklar bir alt kümesi ile her bir .NET uygulaması sağlanır. Temel sınıf kitaplığı (BCL) API'leri geliştiriciler, bunları isteyeceksiniz olduğundan hem popüler kitaplıkları bunları çalıştırmak için gerekeceğinden herhangi bir .NET uygulaması ile beklenir. Uygulamaya özgü kitaplıklar gibi ASP.NET BCL yukarıdaki tüm .NET uygulamalarında kullanılamaz.

## <a name="base-class-libraries"></a>Taban sınıfı kitaplıkları

BCL en temel türleri ve yardımcı işlevleri sağlar ve diğer tüm .NET sınıf kitaplıkları tabanı olan. Tüm iş yükleri için herhangi bir sapma olmadan çok genel uygulamaları sağlamak için hedeflenir. Uygulamalar düşük gecikmeli işleme düzeyi yüksek veya düşük bellek düşük CPU kullanımı gibi belirli bir ilke tercih edebilirsiniz olduğundan performans her zaman önemli bir konu olduğu. Bu kitaplıklar, genellikle yüksek performanslı ve bu çeşitli performans endişelerini göre bir orta taban yaklaşım için tasarlanmıştır. Çoğu uygulama için bu yaklaşım oldukça başarılı olmuştur.

## <a name="primitive-types"></a>İlkel Türler

.NET (farklı derecelerde) bütün programlarda kullanılan ilkel türleri kümesi içerir. Bu türler, sayılar, dizeler, bayt ve rastgele nesneleri gibi verileri içerir. C# Dili anahtar sözcükleri bu türleri içerir. Bu tür bir örnek kümesini, eşleştirme ile aşağıda verilmiştir C# anahtar sözcükleri.

* <xref:System.Object?displayProperty=nameWithType> ([nesne](../csharp/language-reference/keywords/object.md))-temel sınıfta ultimate CLR tür sistemi. Tür hiyerarşisi köküdür.
* <xref:System.Int16?displayProperty=nameWithType> ([kısa](../csharp/language-reference/builtin-types/integral-numeric-types.md))-bir 16-bit imzalı tamsayı türü. İmzasız <xref:System.UInt16> de bulunur.
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/builtin-types/integral-numeric-types.md))-bir 32-bit imzalı tamsayı türü. İmzasız [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) de bulunur.
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/keywords/float.md))-bir 32 bit kayan nokta türü.
* <xref:System.Decimal?displayProperty=nameWithType> ([ondalık](../csharp/language-reference/keywords/decimal.md))-A 128 bit decimal türü.
* <xref:System.Byte?displayProperty=nameWithType> ([bayt](../csharp/language-reference/builtin-types/integral-numeric-types.md))-bir bayt bellek temsil eden bir imzalanmamış 8 bit tam sayı.
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/keywords/bool.md))-gösteren bir Boole türü `true` veya `false`.
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/keywords/char.md))-bir Unicode karakteri temsil eden bir 16 bit sayısal türü.
* <xref:System.String?displayProperty=nameWithType> ([dize](../csharp/language-reference/keywords/string.md))-bir dizi karakteri temsil eder. Farklı bir `char[]`, ancak her bir kişinin dizin oluşturma sağlar `char` içinde `string`.

## <a name="data-structures"></a>Veri yapıları

.NET, neredeyse tüm .NET uygulamalarının iºlerinin olan veri yapılarının bir kümesi içerir. Bunlar çoğunlukla koleksiyonlar, ancak diğer türleri de içerir.

* <xref:System.Array> -Kesin dizin ile ulaşılan türleri nesnelerinin bir dizisini temsil eder. Kendi yapı başına sabit bir boyuta sahiptir.
* <xref:System.Collections.Generic.List%601> -Dizin ile ulaşılan nesneleri türü kesin belirlenmiş bir listesini temsil eder. Gerektiğinde otomatik olarak boyutlandırılır.
* <xref:System.Collections.Generic.Dictionary%602> -Bir anahtarla dizinlenen değerlerin bir koleksiyonunu temsil eder. Değerler, anahtar erişilebilir. Gerektiğinde otomatik olarak boyutlandırılır.
* <xref:System.Uri> -URI'nin bölümlerine kolay erişim ve Tekdüzen Kaynak Tanımlayıcısı (URI) bir nesne temsili sağlar.
* <xref:System.DateTime> -Anlık süre içinde genellikle bir tarih ve saat olarak ifade edilen temsil eder.

## <a name="utility-apis"></a>Yardımcı program API'leri

.NET yardımcı programı, birçok önemli görevler için işlevsellik sağlayan API'ler kümesini içerir.

* <xref:System.Net.Http.HttpClient> -HTTP istekleri göndermek ve bir URI tarafından tanımlanan bir kaynaktan HTTP yanıtları almak için bir API.
* <xref:System.Xml.Linq.XDocument> -Yükleme ve LINQ ile XML belgeleri sorgulama bir API.
* <xref:System.IO.StreamReader> -Dosyaları okuma bir API. 
* <xref:System.IO.StreamWriter> -Dosyalara yazma bir API.

## <a name="app-model-apis"></a>Uygulama modeli API'leri

Birçok uygulama-.NET, çeşitli şirketler tarafından sağlanan ile kullanılabilecek modeli vardır.

* [ASP.NET](https://www.asp.net) -Web siteleri ve hizmetleri oluşturmak için bir web çerçevesi sağlar. Windows, Linux ve Macos'ta (ASP.NET sürümüne bağlıdır) desteklenir.
