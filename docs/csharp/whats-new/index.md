---
title: C# ' - yenilikler C# Kılavuzu
description: C# dili nasıl gelişen
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 399550178a12ff520dff033f0f1dc4a7cdfb9591
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314678"
---
# <a name="whats-new-in-c"></a>C# ' ta yenilikler nelerdir? #

Bu sayfa C# dilinin ana her sürümdeki yeni özelliklerin bir yol haritası sağlar. Aşağıdaki bağlantılar, her sürümde eklenen önemli özellikleri hakkında ayrıntılı bilgi sağlar.

> [!IMPORTANT]
> C# dili türleri ve yöntemleri dayanan bir *standart Kitaplığı* özelliklerinden bazıları için. Özel durum işleme bir örnektir. Her `throw` deyiminin veya ifadesinin işaretli oluşturulan nesne emin olmak için türetilen <xref:System.Exception>. Benzer şekilde, her `catch` yakalanan türü türetilmiş emin olmak için denetlenir <xref:System.Exception>. Her bir sürümü yeni gereksinimler ekleyebilirsiniz. Eski ortamlarda en son dil özellikleri kullanmak için belirli kitaplıkları yüklemeniz gerekebilir. Bu bağımlılıklar, sayfa her belirli bir sürümü için belgelenmiştir. Hakkında daha fazla bilgiyi [dil ve kitaplık arasındaki ilişkileri](relationships-between-language-and-library.md) bu bağımlılığı hakkında arka plan bilgileri için. 

Noktası sürümündeki yeni özellikleri kullanmak için yapmanız [derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçin.

* [C# 7.3](csharp-7-3.md):
  - Bu sayfa, C# dilinde en son özellikleri açıklar. C# 7.3 şu anda kullanılabilir [Visual Studio 2017 sürüm 15.7](https://visualstudio.microsoft.com/vs/whatsnew/)hem de [.NET Core 2.1 SDK 2.1.300 RC1](../../core/whats-new/index.md).
* [C# 7.2](csharp-7-2.md):
  - Bu sayfa C# dilinde eklenen özellikler açıklanmaktadır. C# 7.2 şu anda kullanılabilir [Visual Studio 2017 sürüm 15,5](https://visualstudio.microsoft.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.1](csharp-7-1.md):
  - Bu sayfa, C# 7.1 eklenen özellikler açıklanmaktadır. Bu özellikler eklenmiştir [Visual Studio 2017 sürüm 15.3](https://visualstudio.microsoft.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.0](csharp-7.md):
  - Bu sayfa, C# 7. 0'eklenen özellikler açıklanmaktadır. Bu özellikler eklenmiştir [Visual Studio 2017](https://visualstudio.microsoft.com/vs/whatsnew/) ve [.NET Core 1.0](../../core/whats-new/index.md) ve sonraki sürümler
* [C# 6](csharp-6.md):
  - Bu sayfayı C# 6'eklenen özellikler açıklanmaktadır. Bu özellikler Visual Studio 2015'te .NET Core 1.0 ve Windows geliştiricileri için C# macOS ve Linux keşfetme geliştiriciler için kullanılabilir.
* [Platform desteği arası](../../core/index.md):
  - C# .NET Core desteğini birden çok platformlarında çalışır. Çalışırken ilgileniyorsanız C# macOS veya çok birini desteklenen Linux dağıtımları, .NET Core hakkında daha fazla bilgi edinin.
* [.NET derleme Platform SDK](../roslyn-sdk/index.md):
  - .NET derleme Platform SDK'sı, C# kodu statik çözümleme gerçekleştirir kod yazmanıza olanak sağlar. Olası hataları veya hatalı uygulamaları bulmak, düzeltmeleri önermek ve bu düzeltmeleri bile uygulama için bu API'leri kullanın.

## <a name="previous-versions"></a>Önceki Sürümler

Aşağıdaki listeler dil C# ve Visual Studio .NET önceki sürümlerinde sunulan özellikler anahtar.

* Visual Studio .NET 2013:
  - Visual Studio'nun bu sürümü, hata düzeltmeleri, performans iyileştirmeleri ve hangi hale geldi .NET derleyici Platformu ("Roslyn") teknolojisi önizlemesini dahil [.NET derleyici Platform SDK](../roslyn-sdk/index.md).
* C# 5, Visual Studio .NET 2012:
  - `Async` / `await`, ve [arayan bilgileri](../programming-guide/concepts/caller-information.md) öznitelikleri.
* C# 4, Visual Studio .NET 2010:
  - `Dynamic`, [bağımsız değişkenleri adlı](../programming-guide/classes-and-structs/named-and-optional-arguments.md), isteğe bağlı parametreler ve genel [Kovaryans ve karşıt farkı](../programming-guide/concepts/covariance-contravariance/index.md).
* C# 3, Visual Studio .NET 2008:
  - Nesne ve koleksiyon başlatıcıları, lambda ifadeleri, genişletme yöntemleri, anonim türler, otomatik özellikleri, yerel `var` çıkarım, yazın ve [dil tümleşik sorgu (LINQ)](../programming-guide/concepts/linq/index.md).
* C# 2, Visual Studio .NET 2005:
  - Anonim yöntemler, genel türler, boş değer atanabilir türler, Yineleyiciler/verim `static` sınıfları ve temsilciler Kovaryans ve karşıt varyansını.
* C# 1.1, Visual Studio .NET 2003:
  - `#line` pragma ve xml belge açıklamaları.
* C# 1, Visual Studio .NET 2002:
  - İlk sürümünü [C#](../csharp.md).
