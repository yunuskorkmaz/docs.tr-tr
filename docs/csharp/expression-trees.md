---
title: "İfade Ağaçları"
description: "İfade ağaçları .NET Core ve bunları inceleyin, değiştirme, yürütme ve yapıları olarak kodunu temsil etmek için nasıl kullanılacağı hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 3935906d9fca81a094999eefdd49ae4ed56990bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees"></a>İfade Ağaçları

LINQ kullandıysanız, zengin kitaplığıyla deneyim sahibi olduğu `Func` türleri API kümesi bir parçasıdır. (LINQ ile bilmiyorsanız, büyük olasılıkla okumak istediğiniz [LINQ öğretici](linq/index.md) ve öğretici [lambda ifadeleri](lambda-expressions.md) bundan önce.) *İfade ağaçları* işlevleri olan bağımsız değişkenler daha zengin etkileşim sağlar.

LINQ sorgularını oluşturduğunuzda, genellikle Lambda ifadeleri kullanma işlev bağımsız değişkenleri, yazma. Tipik bir LINQ Sorgu bu işlev bağımsız değişkenleri derleyici oluşturur temsilci dönüştürülür. 

Daha zengin etkileşim olmasını istediğinizde, kullanmanıza gerek *ifade ağaçları*.
İfade ağaçları kodu inceleyin, değiştirme, execute veya bir yapı temsil eder. Bu araçları çalışma zamanı sırasında kodu işlemek için güç sağlar. Çalışan algoritmaları inceler ya da yeni özellikler yerleştirir kod yazabilirsiniz. Daha gelişmiş senaryolarda algoritmaları çalıştıran değiştirmek ve hatta C# başka bir form için başka bir ortamda yürütme ifadelere çevirir.

İfade ağaçları kullanan kodu büyük olasılıkla zaten yazdıktan. Entity Framework'ün LINQ API'ları ifade ağaçları LINQ Sorgu ifade deseni bağımsız değişkenleri olarak kabul eder.
Sağlayan [Entity Framework](http://docs.efproject.net/en/latest/) yazdığınız C# veritabanı altyapısı'nda yürüten SQL içine sorgu çevrilemedi. Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir mocking framework olduğu.

Bu öğreticinin kalan bölümleri ifade ağaçları nelerdir keşfetmek, ifade ağaçları destekleyen ve ifade ağaçları ile nasıl çalışacağınızı framework sınıfları inceleyin. İfade ağaçları okumak nasıl, ifade ağaçları oluşturma, değiştirilmiş ifade ağaçları oluşturma ve ifade ağaçları tarafından temsil edilen kodu çalıştırma hakkında bilgi edineceksiniz. Okuma sonra zengin Uyarlamalı algoritmaları oluşturmak için bu yapıları kullanıma hazır olacaktır.

1. [İfade ağaçları açıklanmıştır](expression-trees-explained.md)

    Yapı ve kavramları anlamanız *ifade ağaçları*.
    
2. [Destek ifade ağaçları Framework türleri](expression-classes.md)
    
    Tanımlayan ve ifade ağaçları işlemek sınıfları ve yapıları hakkında bilgi edinin.
    
3. [Yürütülen ifadeleri](expression-trees-execution.md)

    Lambda ifadesi bir temsilci temsil bir ifade ağacına dönüştürülemiyor öğrenin ve sonuçta elde edilen temsilci yürütün.

4. [İfadeler yorumlama](expression-trees-interpreting.md)

    Çapraz geçiş ve incelemek öğrenin *ifade ağaçları* ne ifade ağacına kod anlamak için temsil eder.

5. [Yapı ifadeleri](expression-trees-building.md)

    Bir ifade ağacına düğümleri oluşturmak ve ifade ağaçları oluşturma hakkında bilgi edinin.

6. [İfadeler çevirme](expression-trees-translating.md)

    Bir ifade ağacına değiştirilmiş bir kopyasını oluşturmak ya da farklı bir biçime bir ifade ağacına çevrilemedi öğrenin.

7. [Özetle](expression-trees-summary.md)

    İfade ağaçları bilgileri gözden geçirin.
    
