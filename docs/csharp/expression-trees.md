---
title: İfade Ağaçları
description: İfade ağaçlarında .NET Core ve bunları kodunu incelemek, değiştirmek, çalıştırmak ve yapıları olarak temsil etmek üzere kullanma hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db6e23d1ad0014a7dbb58a0cd473e67d6bd9acc0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096621"
---
# <a name="expression-trees"></a>İfade Ağaçları

LINQ kullandıysanız, zengin kitaplığı deneyimi olan burada `Func` türleri API kümesi bir parçasıdır. (LINQ ile ilgili bilgi sahibi değilseniz, büyük olasılıkla okumak istediğiniz [LINQ öğretici](linq/index.md) ve ilgili makaleyi [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md) bundan önce.) *İfade ağaçları* işlevleri bağımsız değişkenleriyle daha zengin etkileşim sağlar.

İşlev bağımsız değişkenlerinin, Lambda ifadeleri LINQ sorguları oluşturduğunuzda genellikle kullanarak yazın. Bu işlev bağımsız değişkenleri, tipik bir LINQ Sorgu derleyici oluşturur bir temsilciye dönüştürülür. 

Daha zengin etkileşim görüntülemek istiyorsanız, kullanmanız gereken *ifade ağaçları*.
İfade ağaçları kodunu incelemek, değiştirmek, çalıştırmak veya bir yapı temsil eder. Bu araçlar çalışma zamanı sırasında kod düzenleme olanağı sunar. Çalışan algoritmalar inceler ve yeni özellikleri ekler kod yazabilirsiniz. Daha gelişmiş senaryolarda algoritmaları çalıştıran değiştirebilir ve hatta çevir C# ifadelere başka bir form için başka bir ortamda yürütme.

İfade ağaçları kullanan kodu büyük olasılıkla zaten yazdığınız. Entity Framework'ün LINQ API'leri ifade ağaçları LINQ Sorgu ifade deseni için bağımsız değişkenler olarak kabul eder.
Etkinleştiren [Entity Framework](/ef/) içinde yazdığınız sorgu çevrilecek C# Veritabanı Altyapısı'nda yürütülen SQL içine. Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir sahte işlem altyapısı olduğu.

Bu öğreticinin geri kalan bölümlerini ifade ağaçları nelerdir keşfedin, ifade ağaçlarını destekleyen ve ifade ağaçları ile nasıl Göster framework sınıfları inceleyin. İfade ağaçları okuma, ifade ağaçları oluşturma, değiştirilen ifade ağaçları oluşturma ve ifade ağaçları tarafından temsil edilen kodunun nasıl çalıştırılacağını öğreneceksiniz. Okuma sonra bu yapıları zengin bir Uyarlamalı algoritmalar oluşturmak için kullanılmaya hazır olacaktır.

1. [İfade Ağaçları Açıklaması](expression-trees-explained.md)

    Yapı ve kavramları anlama *ifade ağaçları*.
    
2. [İfade Ağaçlarını Destekleyen Çerçeve Türleri](expression-classes.md)
    
    Yapılar ve sınıflar tanımlayın ve ifade ağaçları işlemek hakkında bilgi edinin.
    
3. [İfade Yürütme](expression-trees-execution.md)

    Bir temsilciye Lambda ifadesiyle temsil edilen bir ifade ağacı dönüştürme hakkında bilgi alın ve sonuç olarak oluşan temsilci yürütün.

4. [İfade Yorumlama](expression-trees-interpreting.md)

    Geçiş ve incelemek öğrenin *ifade ağaçları* ne ifade ağacı kod anlamak için temsil eder.

5. [İfade Derleme](expression-trees-building.md)

    İfade ağacı düğümleri oluşturmak ve ifade ağaçları oluşturma hakkında bilgi edinin.

6. [İfade Çevirme](expression-trees-translating.md)

    İfade ağacı değiştirilmiş bir kopyasını oluşturun veya bir ifade ağacı farklı bir biçime çevir öğrenin.

7. [Özetle](expression-trees-summary.md)

    İfade ağaçları bilgileri gözden geçirin.
