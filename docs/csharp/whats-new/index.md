---
title: İçindeki yenilikler C# - C# Kılavuzu
description: Nasıl olduğunu C# dil gelişen
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: b079c21ee90a797b038b96ae68123a538464c382
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201445"
---
# <a name="whats-new-in-c"></a>C# ' de yenilikler nelerdir? #

Bu sayfa, her ana sürümünün yeni özelliklerin bir yol haritası sağlar. C# dili. Bağlantısı verilen makalelerden her sürümde eklenen önemli özelliklerle ilgili detaylı bilgi ayrıntılı olarak açıklanmaktadır. Genel bir sürüm veya genel önizlemede, yayımlanmış, yeni özellikler hakkında bilgi bulabilirsiniz. Dil özelliği durum, gelecek sürümlerinde bulunabilir kabul özellikleri dahil olmak üzere ayrıntılı [dotnet/roslyn deposundaki](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) GitHub üzerinde.

> [!IMPORTANT]
> C# Dil bağımlı türleri ve yöntemleri bir *standart Kitaplığı* bazı özellikler için. Özel durum işleme bir örnektir. Her `throw` deyiminin veya ifadesinin işaretli oluşturulan nesne emin olmak için türetilen <xref:System.Exception>. Benzer şekilde, her `catch` yakalandı tür türetilir emin olmak için denetlenir <xref:System.Exception>. Her sürüm, yeni gereksinimler ekleyebilirsiniz. En son dil özelliklerini daha eski ortamlarında kullanmak için belirli kitaplıkları yüklemeniz gerekebilir. Bu bağımlılıklar, her belirli bir sürüm sayfasında belgelenmiştir. Daha fazla bilgi edinebilirsiniz [dil ve kitaplığa arasındaki ilişkileri](relationships-between-language-and-library.md) bu bağımlılık hakkında arka plan bilgileri için. 

Bir nokta sürümde en son özellikleri kullanmak için yapmanız [derleyici dil sürüm yapılandırma](../language-reference/configure-language-version.md) ve sürüm seçin.

* [C#7.3](csharp-7-3.md):
  - Bu sayfada en son özellikleri açıklar C# dili. C#7.3 şu anda içinde [Visual Studio 2017 sürüm 15.7](https://visualstudio.microsoft.com/vs/whatsnew/)hem de [.NET Core 2.1 SDK 2.1.300 RC1](../../core/whats-new/index.md).
* [C#7.2](csharp-7-2.md):
  - Bu sayfaya eklenen özellikler açıklanmaktadır C# dili. C#şu anda, 7.2 [Visual Studio 2017 sürüm 15.5](https://visualstudio.microsoft.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK'sını](../../core/whats-new/index.md).
* [C#7.1](csharp-7-1.md):
  - Bu sayfaya eklenen özellikler açıklanmaktadır C# 7.1. Bu özellikler eklenmiştir [Visual Studio 2017 sürüm 15.3](https://visualstudio.microsoft.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK'sını](../../core/whats-new/index.md).
* [C#7.0](csharp-7.md):
  - Bu sayfaya eklenen özellikler açıklanmaktadır C# 7.0. Bu özellikler eklenmiştir [Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) ve [.NET Core 1.0](../../core/whats-new/index.md) ve üzeri
* [C#6](csharp-6.md):
  - Bu sayfa, eklenen özellikler açıklanmaktadır C# 6. Bu özellikler için keşfetmek geliştiriciler Visual Studio 2015'te .NET Core 1.0 ve Windows geliştiricileri için kullanılabilir C# macOS ve Linux'ta.
* [Çapraz platform desteği](../../core/index.md):
  - C#, .NET Core desteği, birden çok platformda çalıştırır. Çalışırken ilgileniyorsanız C# macOS üzerinde desteklenen çok birini veya Linux dağıtımları hakkında daha fazla bilgi .NET Core.
* [.NET derleyici Platformu SDK](../roslyn-sdk/index.md):
  - .NET derleyici Platformu SDK'sı statik analiz gerçekleştirir kod yazmanızı sağlar C# kod. Olası hataları veya hatalı uygulamaları bulmak için düzeltmeler önerir ve bile bu düzeltmeleri uygulayabilirsiniz, bu API'leri kullanabilirsiniz.

## <a name="previous-versions"></a>Önceki Sürümler

Aşağıdaki önceki sürümlerinde sunulan anahtar özelliklerini listeler C# dil ve Visual Studio.

* Visual Studio 2013 .NET:
  - Visual Studio'nun bu sürümü, hata düzeltmeleri ve performans iyileştirmeleri teknoloji önizlemeleri, dönüştü .NET derleyici Platformu ("Roslyn") dahil [.NET derleyici Platformu SDK'sı](../roslyn-sdk/index.md).
* C#5, visual Studio .NET 2012:
  - `Async` / `await`, ve [arayan bilgileri](../programming-guide/concepts/caller-information.md) öznitelikleri.
* C#4, visual Studio 2010 .NET:
  - `Dynamic`, [adlandırılmış bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md), isteğe bağlı parametreler ve genel [Kovaryans ve karşıt varyansı](../programming-guide/concepts/covariance-contravariance/index.md).
* C#3, visual Studio 2008 .NET:
  - Nesne ve koleksiyon başlatıcıları, lambda ifadeleri, genişletme yöntemleri, anonim türler, otomatik özellikleri, yerel `var` anlam çıkarma, ve [dil tümleşik sorgu (LINQ)](../programming-guide/concepts/linq/index.md).
* C#2, visual Studio .NET 2005:
  - Anonim yöntemler, genel türler, boş değer atanabilir türler, Yineleyiciler/yield `static` sınıfları ve temsilciler için Kovaryans ve karşıt farkı.
* C#1.1, visual Studio .NET 2003:
  - `#line` pragma ve xml belge açıklamaları.
* C#1, visual Studio .NET 2002:
  - İlk sürümü [ C# ](../csharp.md).
