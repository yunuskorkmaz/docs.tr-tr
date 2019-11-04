---
title: Framework Kitaplıkları
description: Kitaplıkların birçok genel ve uygulamaya özel türler, algoritmalar ve yardımcı program işlevselliğine yönelik uygulamalar sağladığını öğrenin.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: 9c0b5a07277de6e87e2692ebb7c4f73c03702801
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424965"
---
# <a name="framework-libraries"></a>Framework Kitaplıkları

.NET, temel sınıf kitaplıkları (çekirdek kümesi) veya çerçeve sınıfı kitaplıkları (tüm küme) olarak adlandırılan, expantik standart sınıf kitaplıkları kümesine sahiptir. Bu kitaplıklar birçok genel ve uygulamaya özel türler, algoritmalar ve yardımcı program işlevselliğine yönelik uygulamalar sağlar. Hem ticari hem de topluluk kitaplıkları, geniş bir bilgi işlem görevleri için raf dışı kitaplıkların kolayca kullanılmasını sağlayan Framework sınıf kitaplıklarının üzerine inşa.

Bu kitaplıkların bir alt kümesi, her .NET uygulamasıyla birlikte sağlanır. Temel sınıf kitaplığı (BCL) API 'Lerinde her ikisi de her türlü .NET uygulamasıyla beklenmektedir, çünkü geliştiriciler istedikleri gibi popüler kitaplıkların çalışmasına gerek duyar. ASP.NET gibi BCL üzerindeki uygulamaya özgü kitaplıklar, tüm .NET uygulamalarında kullanılamaz.

## <a name="base-class-libraries"></a>Temel sınıf kitaplıkları

BCL en temel tür ve yardımcı program işlevlerini sağlar ve diğer tüm .NET sınıf kitaplıklarının temelini içerir. Tüm iş yükleri için herhangi bir sapma olmadan çok genel uygulamalar sağlamayı hedefler. Uygulamalar belirli bir ilkeyi tercih edebileceğinizden, yüksek aktarım hızı veya düşük bellekli düşük CPU kullanımı için düşük gecikme süresine sahip olduğundan performans her zaman önemli bir noktadır. Bu kitaplıkların genellikle yüksek performanslı olması amaçlanmıştır ve bu çeşitli performans sorunlarına göre orta bir yaklaşım ele alınır. Çoğu uygulama için bu yaklaşım oldukça başarılı olmuştur.

## <a name="primitive-types"></a>İlkel Türler

.NET, tüm programlarda kullanılan (farklı derecelerde) bir temel türler kümesi içerir. Bu türler sayılar, dizeler, baytlar ve rastgele nesneler gibi verileri içerir. Dil C# , bu türlerin anahtar sözcüklerini içerir. Bu türlerin örnek bir kümesi, eşleşen C# anahtar sözcüklerle aşağıda listelenmiştir.

* <xref:System.Object?displayProperty=nameWithType> ([nesne](../csharp/language-reference/builtin-types/reference-types.md#the-object-type))-clr türü sistemindeki en son temel sınıf. Bu, tür hiyerarşisinin köküdür.
* <xref:System.Int16?displayProperty=nameWithType> ([kısa](../csharp/language-reference/builtin-types/integral-numeric-types.md))-16 bit işaretli bir tamsayı türü. İmzasız <xref:System.UInt16> de mevcuttur.
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/builtin-types/integral-numeric-types.md))-32 bitlik işaretli bir tamsayı türü. İmzasız [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) de mevcuttur.
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/builtin-types/floating-point-numeric-types.md))-bir 32 bit kayan nokta türü.
* <xref:System.Decimal?displayProperty=nameWithType> ([Decimal](../csharp/language-reference/builtin-types/floating-point-numeric-types.md))-128 bit ondalık türü.
* <xref:System.Byte?displayProperty=nameWithType> ([bayt](../csharp/language-reference/builtin-types/integral-numeric-types.md))-belleğin bir baytını temsil eden işaretsiz 8 bitlik bir tamsayı.
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/keywords/bool.md))-`true` veya `false`temsil eden bir Boole türü.
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/keywords/char.md))-Unicode karakteri temsil eden 16 bit sayısal bir tür.
* <xref:System.String?displayProperty=nameWithType> ([dize](../csharp/language-reference/builtin-types/reference-types.md#the-string-type))-bir karakter dizisini temsil eder. `char[]`farklıdır, ancak `string`her tekil `char` Dizin oluşturmayı mümkün hale getirmenizi.

## <a name="data-structures"></a>Veri yapıları

.NET, neredeyse tüm .NET uygulamalarının iş atları olan bir veri yapıları kümesi içerir. Bunlar genellikle koleksiyonlardır, ancak diğer türleri de içerir.

* <xref:System.Array>-dizin tarafından erişilebilen kesin türler nesnelerinin dizisini temsil eder. , Oluşturma başına sabit bir boyuta sahiptir.
* <xref:System.Collections.Generic.List%601>-dizin tarafından erişilebilen nesnenin türü kesin belirlenmiş bir listesini temsil eder. Gerektiğinde otomatik olarak yeniden boyutlandırılır.
* <xref:System.Collections.Generic.Dictionary%602>-bir anahtar tarafından dizine eklenen değerlerin koleksiyonunu temsil eder. Değerlere anahtar aracılığıyla erişilebilir. Gerektiğinde otomatik olarak yeniden boyutlandırılır.
* <xref:System.Uri>-Tekdüzen Kaynak tanımlayıcısı 'nın (URI) nesne gösterimini ve URI 'nin bölümlerine kolay erişim sağlar.
* <xref:System.DateTime>-genellikle günün tarih ve saati olarak ifade edilen bir anlık zaman temsil eder.

## <a name="utility-apis"></a>Yardımcı program API 'Leri

.NET birçok önemli görev için işlevsellik sağlayan bir yardımcı program API 'Leri içerir.

* <xref:System.Net.Http.HttpClient>-HTTP istekleri göndermeye ve URI tarafından tanımlanan bir kaynaktan HTTP yanıtlarını almaya yönelik bir API.
* <xref:System.Xml.Linq.XDocument>-LINQ ile XML belgelerini yüklemek ve sorgulamak için bir API.
* <xref:System.IO.StreamReader>-dosyaları okumak için bir API. 
* <xref:System.IO.StreamWriter>-dosya yazmak için bir API.

## <a name="app-model-apis"></a>Uygulama modeli API 'Leri

Çeşitli şirketler tarafından sunulan .NET ile kullanılabilen birçok uygulama modeli vardır.

* [ASP.net](https://www.asp.net) -Web siteleri ve hizmetleri oluşturmak için bir Web çerçevesi sağlar. Windows, Linux ve macOS 'ta desteklenir (ASP.NET sürümüne bağlıdır).
