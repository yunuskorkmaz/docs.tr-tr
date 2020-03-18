---
title: Framework Kitaplıkları
description: Kitaplıkların birçok genel ve uygulamaya özgü tür, algoritma ve yardımcı program işlevselliği için nasıl uygulama sağladığını öğrenin.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: d4444b6d080afa92a4e7fd9f30c5f9358f02f0ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159240"
---
# <a name="framework-libraries"></a>Framework Kitaplıkları

.NET'in taban sınıf kitaplıkları (çekirdek kümesi) veya framework class kitaplıkları (tam küme) olarak adlandırılan geniş bir standart sınıf kitaplıkları kümesi vardır. Bu kitaplıklar, birçok genel ve uygulamaya özgü türler, algoritmalar ve yardımcı program işlevleri için uygulamalar sağlar. Hem ticari hem de topluluk kitaplıkları, çok çeşitli bilgi işlem görevleri için kullanımı kolay olan çerçeve sınıfı kitaplıklarının üzerine inşa edin.

Bu kitaplıkların bir alt kümesi her .NET uygulaması yla sağlanır. Temel Sınıf Kitaplığı (BCL) API'leri, hem geliştiriciler bunları isteyeceğinden hem de popüler kitaplıkların çalışmasına gerek yacağı için herhangi bir .NET uygulamasıyla birlikte beklenmektedir. ASP.NET gibi BCL'nin üzerindeki uygulamaya özgü kitaplıklar tüm .NET uygulamalarında kullanılamaz.

## <a name="base-class-libraries"></a>Taban Sınıf Kütüphaneleri

BCL en temel türleri ve yardımcı program işlevselliği sağlar ve diğer tüm .NET sınıf kitaplıklarının temelini oluşturur. Onlar herhangi bir iş yükü herhangi bir önyargı olmadan çok genel uygulamalar sağlamayı hedefliyoruz. Uygulamalar düşük gecikme lisi ile yüksek işlemci kullanımı veya düşük bellek ve düşük CPU kullanımı gibi belirli bir ilkeyi tercih edebileceğinden, performans her zaman önemli bir husustur. Bu kütüphaneler genellikle yüksek performanslı olması ve bu çeşitli performans endişelerine göre orta zemin yaklaşımı benimsenmesi amaçlanmıştır. Çoğu uygulama için bu yaklaşım oldukça başarılı olmuştur.

## <a name="primitive-types"></a>İlkel Türler

.NET, tüm programlarda kullanılan (değişik derecelerde) ilkel türleri içerir. Bu türler sayılar, dizeleri, baytlar ve rasgele nesneler gibi verileri içerir. C# dili, bu tür için anahtar kelimeler içerir. Bu türlerden bir örnek kümesi, eşleşen C# anahtar kelimeleri ile aşağıda listelenmiştir.

* <xref:System.Object?displayProperty=nameWithType>([object](../csharp/language-reference/builtin-types/reference-types.md#the-object-type)) - CLR türü sistemindeki nihai taban sınıf. Tür hiyerarşisinin köküdür.
* <xref:System.Int16?displayProperty=nameWithType>([kısa](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - 16 bit imzalı tamsayı türü. İmzasız <xref:System.UInt16> da var.
* <xref:System.Int32?displayProperty=nameWithType>([int](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - 32 bit imzalı tamsayı türü. İmzasız [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) de vardır.
* <xref:System.Single?displayProperty=nameWithType>([float](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) - 32-bit kayan nokta türü.
* <xref:System.Decimal?displayProperty=nameWithType>([ondalık](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) - A 128-bit ondalık türü.
* <xref:System.Byte?displayProperty=nameWithType>([bayt](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - Bir bayt bellek temsil eden imzasız 8-bit tamsayı.
* <xref:System.Boolean?displayProperty=nameWithType>([bool](../csharp/language-reference/builtin-types/bool.md)) - Temsil `true` eden `false`bir Boolean türü ya .
* <xref:System.Char?displayProperty=nameWithType>([char](../csharp/language-reference/builtin-types/char.md)) - Unicode karakterini temsil eden 16 bitlik sayısal bir tür.
* <xref:System.String?displayProperty=nameWithType>([string](../csharp/language-reference/builtin-types/reference-types.md#the-string-type)) - Bir karakter serisini temsil eder. Bir `char[]`'den farklı, ancak her `char` bir `string`bireye indeksleme sağlar.

## <a name="data-structures"></a>Veri Yapıları

.NET, hemen hemen tüm .NET uygulamalarının çalışma atları olan bir veri yapıları kümesi içerir. Bunlar çoğunlukla koleksiyonlar, ancak diğer türleri de içerir.

* <xref:System.Array>- Dizin tarafından erişilebilen güçlü türdeki nesnelerdizisini temsil eder. Yapısına göre sabit bir boyutu vardır.
* <xref:System.Collections.Generic.List%601>- Dizin tarafından erişilebilen nesnelerin güçlü bir şekilde yazılan listesini temsil eder. Gerektiğinde otomatik olarak yeniden boyutlandırılır.
* <xref:System.Collections.Generic.Dictionary%602>- Bir anahtar tarafından dizine eklenmiş değerler koleksiyonunu temsil eder. Değerlere anahtarla erişilebilir. Gerektiğinde otomatik olarak yeniden boyutlandırılır.
* <xref:System.Uri>- Tek tip bir kaynak tanımlayıcısının (URI) nesne gösterimi ve URI'nin bölümlerine kolay erişim sağlar.
* <xref:System.DateTime>- Genellikle günün tarihi ve saati olarak ifade edilen, zaman içinde bir an temsil eder.

## <a name="utility-apis"></a>Yardımcı Program API'leri

.NET, birçok önemli görev için işlevsellik sağlayan bir dizi yardımcı program API içerir.

* <xref:System.Net.Http.HttpClient>- HTTP isteklerini göndermek ve BIR URI tarafından tanımlanan bir kaynaktan HTTP yanıtları almak için bir API.
* <xref:System.Xml.Linq.XDocument>- XML belgelerinin LINQ ile yüklenmesi ve sorgulanması için bir API.
* <xref:System.IO.StreamReader>- Dosyaları okumak için bir API.
* <xref:System.IO.StreamWriter>- Dosya yazmak için bir API.

## <a name="app-model-apis"></a>Uygulama Modeli API'leri

.NET ile kullanılabilen ve birçok şirket tarafından sağlanan birçok uygulama modeli vardır.

* [ASP.NET](https://www.asp.net) - Web siteleri ve hizmetleri oluşturmak için bir web çerçevesi sağlar. Windows, Linux ve macOS'ta desteklenir (ASP.NET sürümüne bağlıdır).
