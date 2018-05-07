---
title: İfade Ağaçları
description: İfade ağaçları .NET Core ve bunları inceleyin, değiştirme, yürütme ve yapıları olarak kodunu temsil etmek için nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db35dd99dadc4e49aaaebd5d3782409a206cafc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees"></a>İfade Ağaçları

LINQ kullandıysanız, zengin kitaplığıyla deneyim sahibi olduğu `Func` türleri API kümesi bir parçasıdır. (LINQ ile bilmiyorsanız, büyük olasılıkla okumak istediğiniz [LINQ öğretici](linq/index.md) ve öğretici [lambda ifadeleri](lambda-expressions.md) bundan önce.) *İfade ağaçları* işlevleri olan bağımsız değişkenler daha zengin etkileşim sağlar.

LINQ sorgularını oluşturduğunuzda, genellikle Lambda ifadeleri kullanma işlev bağımsız değişkenleri, yazma. Tipik bir LINQ Sorgu bu işlev bağımsız değişkenleri derleyici oluşturur temsilci dönüştürülür. 

Daha zengin etkileşim olmasını istediğinizde, kullanmanıza gerek *ifade ağaçları*.
İfade ağaçları kodu inceleyin, değiştirme, execute veya bir yapı temsil eder. Bu araçları çalışma zamanı sırasında kodu işlemek için güç sağlar. Çalışan algoritmaları inceler ya da yeni özellikler yerleştirir kod yazabilirsiniz. Daha gelişmiş senaryolarda algoritmaları çalıştıran değiştirmek ve hatta C# başka bir form için başka bir ortamda yürütme ifadelere çevirir.

İfade ağaçları kullanan kodu büyük olasılıkla zaten yazdıktan. Entity Framework'ün LINQ API'ları ifade ağaçları LINQ Sorgu ifade deseni bağımsız değişkenleri olarak kabul eder.
Sağlayan [Entity Framework](http://docs.efproject.net/en/latest/) yazdığınız C# veritabanı altyapısı'nda yürüten SQL içine sorgu çevrilemedi. Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir mocking framework olduğu.

Bu öğreticinin kalan bölümleri ifade ağaçları nelerdir keşfetmek, ifade ağaçları destekleyen ve ifade ağaçları ile nasıl çalışacağınızı framework sınıfları inceleyin. İfade ağaçları okumak nasıl, ifade ağaçları oluşturma, değiştirilmiş ifade ağaçları oluşturma ve ifade ağaçları tarafından temsil edilen kodu çalıştırma hakkında bilgi edineceksiniz. Okuma sonra zengin Uyarlamalı algoritmaları oluşturmak için bu yapıları kullanıma hazır olacaktır.

1. [İfade Ağaçları Açıklaması](expression-trees-explained.md)

    Yapı ve kavramları anlamanız *ifade ağaçları*.
    
2. [İfade Ağaçlarını Destekleyen Çerçeve Türleri](expression-classes.md)
    
    Tanımlayan ve ifade ağaçları işlemek sınıfları ve yapıları hakkında bilgi edinin.
    
3. [İfade Yürütme](expression-trees-execution.md)

    Lambda ifadesi bir temsilci temsil bir ifade ağacına dönüştürülemiyor öğrenin ve sonuçta elde edilen temsilci yürütün.

4. [İfade Yorumlama](expression-trees-interpreting.md)

    Çapraz geçiş ve incelemek öğrenin *ifade ağaçları* ne ifade ağacına kod anlamak için temsil eder.

5. [İfade Derleme](expression-trees-building.md)

    Bir ifade ağacına düğümleri oluşturmak ve ifade ağaçları oluşturma hakkında bilgi edinin.

6. [İfade Çevirme](expression-trees-translating.md)

    Bir ifade ağacına değiştirilmiş bir kopyasını oluşturmak ya da farklı bir biçime bir ifade ağacına çevrilemedi öğrenin.

7. [Özetle](expression-trees-summary.md)

    İfade ağaçları bilgileri gözden geçirin.
    
