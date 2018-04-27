---
title: C# ' - yenilikler C# Kılavuzu
description: C# dili nasıl gelişen
keywords: C#, yenilikler, en son özellikleri Roslyn
author: BillWagner
ms.author: wiwagn
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: d66f835d57f43d2016d3b20e2205e0052d064acb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="whats-new-in-c"></a>C# ' ta yenilikler nelerdir? #

Bu sayfa C# dilinin ana her sürümdeki yeni özelliklerin bir yol haritası sağlar. Aşağıdaki bağlantılar, her sürümde eklenen önemli özellikleri hakkında ayrıntılı bilgi sağlar.

> [!IMPORTANT]
> C# dili türleri ve yöntemleri dayanan bir *standart Kitaplığı* özelliklerinden bazıları için. Özel durum işleme bir örnektir. Her `throw` deyiminin veya ifadesinin işaretli oluşturulan nesne emin olmak için türetilen <xref:System.Exception>. Benzer şekilde, her `catch` yakalanan türü türetilmiş emin olmak için denetlenir <xref:System.Exception>. Her bir sürümü yeni gereksinimler ekleyebilirsiniz. Eski ortamlarda en son dil özellikleri kullanmak için belirli kitaplıkları yüklemeniz gerekebilir. Bu bağımlılıklar, sayfa her belirli bir sürümü için belgelenmiştir. Hakkında daha fazla bilgiyi [dil ve kitaplık arasındaki ilişkileri](relationships-between-language-and-library.md) bu bağımlılığı hakkında arka plan bilgileri için. 


* [C# 7.2](csharp-7-2.md):
    - Bu sayfa, C# dilinde en son özellikleri açıklar. C# 7.2 şu anda kullanılabilir [Visual Studio 2017 sürüm 15,5](https://www.visualstudio.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK](../../core/whats-new/index.md).

* [C# 7.1](csharp-7-1.md):
    - Bu sayfa, C# 7.1 özellikleri açıklanmıştır. Bu özellikler eklenmiştir [Visual Studio 2017 sürüm 15.3](https://www.visualstudio.com/vs/whatsnew/)hem de [.NET Core 2.0 SDK](../../core/whats-new/index.md).

* [C# 7.0](csharp-7.md):
    - Bu sayfa, C# 7. 0'eklenen özellikler açıklanmaktadır. Bu özellikler eklenmiştir [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) ve [.NET Core 1.0](../../core/whats-new/index.md) ve sonraki sürümler
     
* [C# 6](csharp-6.md):
    - Bu sayfayı C# 6'eklenen özellikler açıklanmaktadır. Bu özellikler Visual Studio 2015'te .NET Core 1.0 ve Windows geliştiricileri için C# macOS ve Linux keşfetme geliştiriciler için kullanılabilir.

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* [Platform desteği arası](../../core/index.md):
    - C# .NET Core desteğini birden çok platformlarında çalışır. Çalışırken ilgileniyorsanız C# macOS veya çok birini desteklenen Linux dağıtımları, .NET Core hakkında daha fazla bilgi edinin.

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a>Önceki Sürümler
Aşağıdaki listeler dil C# ve Visual Studio .NET önceki sürümlerinde sunulan özellikler anahtar.  
  
 * Visual Studio .NET 2013: 
     - Visual Studio'nun bu sürümü, hata düzeltmeleri, performans iyileştirmeleri ve hangi .NET derleyici Platform SDK'sı hale geldi .NET derleyici Platformu ("Roslyn") teknolojisi önizlemesini dahil<!--Link to ../roslyn/index.md-->.

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
