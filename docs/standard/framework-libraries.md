---
title: Framework kitaplıkları
description: Birçok genel ve uygulamaya özgü türleri, algoritmalar ve yardımcı programı işlevselliği kitaplıkları uygulamaları nasıl sağladığını öğrenin.
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: dd8baa481e51aa44c4c884b4b165bdf319ac1c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="framework-libraries"></a>Framework kitaplıkları

.NET sınıf kitaplıkları için temel sınıf kitaplıkları (çekirdek kümesi) veya framework sınıf kitaplıkları (eksiksiz) olarak adlandırılan bir korunmalarını standart kümesi vardır. Bu kitaplıklar, birçok genel ve uygulamaya özgü türleri, algoritmalar ve yardımcı programı işlevselliği için uygulamaları sağlar. Bilgisayar işlemleri geniş kümesi için kullanımı kolay piyasada kitaplıkları sağlama framework sınıf kitaplıkları üstünde hem ticari hem de topluluk kitaplıkları oluşturun.

Bu kitaplıklar kümesini her bir .NET uygulama ile sağlanır. Taban sınıf kitaplığı (BCL) API geliştiricilere bunları isteyeceksiniz çünkü hem popüler kitaplıkları çalıştırmalarını gerekir çünkü herhangi bir .NET uygulaması ile beklenir. Uygulamaya özgü kitaplıkları ASP.NET gibi BCL yukarıdaki tüm .NET uygulamalarında kullanılabilir olmaz.

## <a name="base-class-libraries"></a>Taban sınıf kitaplıkları

BCL ve diğer .NET sınıf kitaplıkları tabanı olan en temel türleri ve yardımcı işlevleri sağlar. Herhangi bir iş yükü hiçbir sapmaya olmadan çok genel uygulamalarını hedefleyin. Uygulamalar düşük gecikme süreli yüksek verimlilik için veya düşük bellek içi düşük CPU kullanımı gibi belirli bir ilkenin tercih edebilirsiniz beri performans her zaman önemli bir konu olduğu. Bu kitaplıklar, genellikle yüksek performanslı ve bu çeşitli performans sorunları göre Orta başından başlayarak yaklaşımı üzere tasarlanmıştır. Çoğu uygulamalar için bu yaklaşım oldukça başarılı olmuştur.

## <a name="primitive-types"></a>İlkel Türler

.NET (farklı derecelerde) tüm programları ile kullanılan ilkel türler içerir. Bu tür numaraları, dizeleri, bayt ve rasgele nesneler gibi verileri içerir. C# dili, bu tür için anahtar sözcükleri içerir. Bu tür bir örnek kümesini eşleşen C# anahtar sözcükleri ile aşağıda listelenir.

* <xref:System.Object?displayProperty=nameWithType> ([nesne](../csharp/language-reference/keywords/object.md))-CLR ultimate temel sınıfında sistem yazın. Tür hiyerarşisini köküdür.
* <xref:System.Int16?displayProperty=nameWithType> ([kısa](../csharp/language-reference/keywords/short.md))-bir 16 bit imzalı tamsayı türü. İmzasız <xref:System.UInt16> de bulunur.
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/keywords/int.md))-bir 32 bit imzalı tamsayı türü. İmzasız [UInt32](../csharp/language-reference/keywords/uint.md) de bulunur.
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/keywords/float.md))-bir 32 bit kayan nokta türü.
* <xref:System.Decimal?displayProperty=nameWithType> ([ondalık](../csharp/language-reference/keywords/decimal.md))-A 128-bit decimal türü.
* <xref:System.Byte?displayProperty=nameWithType> ([bayt](../csharp/language-reference/keywords/byte.md))-bayt bellek temsil eden bir imzasız 8 bit tam sayı.
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/keywords/bool.md))-gösteren bir boolean türü `true` veya `false`.
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/keywords/char.md))-Unicode karakteri temsil eden bir 16 bit sayısal tür.
* <xref:System.String?displayProperty=nameWithType> ([dize](../csharp/language-reference/keywords/string.md))-bir karakter dizisi temsil eder. Farklı bir `char[]`, ancak her dizin oluşturma sağlar `char` içinde `string`.

## <a name="data-structures"></a>Veri yapıları

.NET neredeyse her .NET uygulamalarını iºlerinin olan veri yapılarını kümesi içerir. Bunlar çoğunlukla koleksiyonlar, ancak aynı zamanda diğer türleri içerir.

*   <xref:System.Array> -Kesinlikle dizini tarafından erişilebilen türleri nesnelerinin bir dizisi temsil eder. Kendi yapım başına sabit bir boyutu vardır.
*   <xref:System.Collections.Generic.List%601> -Kesin türü belirtilmiş dizini tarafından erişilebilecek nesnelerin listesini temsil eder. Gerektiğinde otomatik olarak boyutlandırılır.
*   <xref:System.Collections.Generic.Dictionary%602> -Bir anahtar dizini değerleri koleksiyonunu temsil eder. Değerleri anahtarı erişilebilir. Gerektiğinde otomatik olarak boyutlandırılır.
*   <xref:System.Uri> -URI'SİNİN bölümlerini bir nesne temsili bir Tekdüzen Kaynak Tanımlayıcısı (URI) ve kolay erişim sağlar.
*   <xref:System.DateTime> -Anında, zaman içindeki genellikle bir tarih ve saat ifade edilen temsil eder.

## <a name="utility-apis"></a>Yardımcı programı API'leri

.NET yardımcı işlevleri sağlamak için birçok önemli görevleri API kümesini içerir.

*   <xref:System.Net.Http.HttpClient> -HTTP istekleri göndermek ve bir URI tarafından tanımlanan bir kaynaktan HTTP yanıtları almak için bir API.
*   <xref:System.Xml.Linq.XDocument> -Yükleme ve LINQ ile XML belgelerini sorgulamak için bir API.
*   <xref:System.IO.StreamReader> -Dosyaları okuma bir API (<xref:System.IO.StringWriter>) dosyaları yazmak için kullanılır.

## <a name="app-model-apis"></a>Uygulama modeli API'leri

Birçok uygulama-çeşitli şirketler tarafından sağlanan .NET ile kullanılan model vardır.

*   [ASP.NET](http://asp.net) -Web siteleri ve hizmetleri oluşturmak için bir web çerçevesidir sağlar. Windows, Linux ve macOS (ASP.NET sürüme bağlıdır) desteklenir.
