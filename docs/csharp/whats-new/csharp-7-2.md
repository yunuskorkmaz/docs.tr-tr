---
title: C# 7.2 yenilikler nelerdir?
description: "C# 7.2 yeni özellikleri genel bakış."
keywords: "C# dil tasarımında, 7.2, Visual Studio 2017,"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: db22c9251fa5e9f5a9cb66af6ec8b193b88e0eb3
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="whats-new-in-c-72"></a>C# 7.2 yenilikler nelerdir?

C# 7.2 çok sayıda kullanışlı özelliği ekleyen başka bir nokta sürümüdür.
Bu sürüm için bir tema, gereksiz kopya veya ayırmaları kaçınarak değer türleri ile daha verimli bir şekilde çalışıyor. 

Kalan özellikler küçük, olması iyi özelliklerdir.

C# 7.2 kullanan [dil sürümü seçimi](csharp-7-1.md#language-version-selection) yapılandırma öğesi derleyici dil sürümünü seçin.

Bu sürümdeki yeni diz özellikleri şunlardır:

* [Değer türleri ile başvuru semantiği](#reference-semantics-with-value-types)
  - Başvuru anlamsallarını kullanarak değer türleri ile çalışmayı etkinleştirmek sözdizimi geliştirmeleri birleşimi.
* [Olmayan sondaki-adlandırılmış bağımsız değişkenler](#non-trailing-named-arguments)
  - Adlandırılmış bağımsız değişkenler konumsal değişkenleriyle izlenebilir.
* [Sayısal değişmez değerlerinde başında alt çizgiler](#leading-underscores-in-numeric-literals)
  - Sayısal değişmez değerler artık yazdırılan herhangi bir rakam önce başında alt çizgi olabilir.
* [`private protected` Erişim değiştiricisi](#private-protected-access-modifier)
  - `private protected` Erişim değiştiricisi aynı bütünleştirilmiş kodda türetilmiş sınıfları için erişim sağlar.

## <a name="reference-semantics-with-value-types"></a>Başvuru semantiği ile değer türleri

7.2 içinde sunulan dil özellikleri başvurusu semantiği kullanırken değer türleri ile çalışmanıza olanak tanır. Başvuru türleri kullanımıyla ilişkili bellek ayırmaları yansıtılmasını olmadan kopyalama değer türleri en aza performansı artırmak için tasarlanmıştır. Özellikleri içerir:

 - `in` Bağımsız değişken başvuruyla geçirildi ancak çağrılan yöntemi tarafından değiştirilmeyen belirtmek üzere parametreler, değiştiricisi.
 - `ref readonly` Değiştiricisi bir yöntem başvuruya göre değerini döndürür ancak o nesnenin yazmaları izin vermeyen belirtmek için yöntemi döndürür.
 - `readonly struct` Yapı sabittir ve olarak iletilmesi gereken göstermek için bildirim, bir `in` üye yöntemlerinden parametresi.
 - `ref struct` Bir yapı türü yönetilen bellek doğrudan erişir ve her zaman ayrılmış yığın göstermek için bildirim.

Tüm bunlar hakkında daha fazla bilgi için değişiklikler okuyabilirsiniz [başvuru semantiği ile değer türleri kullanarak](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Olmayan sondaki-adlandırılmış bağımsız değişkenler

Yöntem çağrıları şimdi bu bağımsız değişken adlı doğru konumda olduğunda, konumsal bağımsız değişkenleri koyun adlandırılmış bağımsız değişkenler kullanabilirsiniz. Daha fazla bilgi için bkz: [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Sayısal değişmez değerlerinde başında alt çizgiler

C# 7.0 basamak ayırıcıları desteği uyarlamasını izin kaydetmedi `_` ilk karakter değişmez değeri olmalıdır. Onaltılık ve ikili sayısal değişmez değerleri şimdi başlamak ile bir `_`. 

Örneğin:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>_korumalı özel_ erişim değiştiricisi

Son olarak, yeni bir bileşik erişim değiştiricisi: `private protected` üyesi sınıfı ya da aynı bütünleştirilmiş kodda bildirilen türetilen sınıflar içeren tarafından erişilebileceği gösterir. Sırada `protected internal` türetilen sınıflar ya da aynı bütünleştirilmiş kodda olan sınıfları tarafından erişime izin veren `private protected` aynı bütünleştirilmiş kodda bildirilen türetilmiş türler erişimi sınırlar.

Daha fazla bilgi için bkz: [erişim değiştiricileri](../language-reference/keywords/access-modifiers.md) dil başvurusu.
