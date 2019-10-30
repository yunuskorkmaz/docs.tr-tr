---
title: İfade Ağaçları
description: .NET Core 'daki ifade ağaçları ve kodu, inceleyebileceğiniz, değiştirebileceğiniz ve yürütemeyeceğiniz yapılar olarak göstermek için nasıl kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7d039ea4585953473dc88cebcc516ea240cdc3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036316"
---
# <a name="expression-trees"></a>İfade Ağaçları

LINQ kullandıysanız, `Func` türlerinin API kümesinin bir parçası olduğu zengin bir kitaplık ile karşılaşırsınız. (LINQ hakkında bilginiz yoksa, büyük olasılıkla [LINQ öğreticisini](linq/index.md) ve bu uygulamadan önce [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md) hakkındaki makaleyi okumak istersiniz.) *Ifade ağaçları* , işlevleri olan bağımsız değişkenlerle daha zengin etkileşim sağlar.

LINQ sorguları oluştururken, genellikle lambda Ifadeleri kullanarak işlev bağımsız değişkenleri yazarsınız. Tipik bir LINQ sorgusunda, bu işlev bağımsız değişkenleri derleyicinin oluşturduğu bir temsilciye dönüştürülür. 

Daha zengin bir etkileşim sağlamak istediğinizde, *Ifade ağaçları*kullanmanız gerekir.
İfade ağaçları kodu, inceleyebileceğiniz, değiştirebileceğiniz veya yürütebilmeniz için bir yapı olarak temsil eder. Bu araçlar, çalışma zamanında kodu işleme gücü sağlar. Çalışan algoritmaların incelediği veya yeni özellikleri barındıran bir kod yazabilirsiniz. Daha Gelişmiş senaryolarda, çalışan algoritmaları değiştirebilir ve hatta farklı bir ortamda yürütmek üzere C# ifadeleri başka bir biçimde çevirebilirsiniz.

Büyük olasılıkla Ifade ağaçları kullanan kodu zaten yazmış olabilirsiniz. Entity Framework LINQ API 'Leri, LINQ sorgu Ifade deseninin bağımsız değişkenleri olarak Ifade ağaçlarını kabul eder.
Bu, [Entity Framework](/ef/) , yazdığınız sorguyu veritabanı ALTYAPıSıNDA yürütülen SQL C# 'e çevirmesini sağlar. .NET için popüler bir sahte işlem çerçevesi olan [moq](https://github.com/Moq/moq)başka bir örnektir.

Bu öğreticinin geri kalan bölümleri, Ifade ağaçlarının ne olduğunu keşfedebilir, ifade ağaçlarını destekleyen çerçeve sınıflarını inceler ve ifade ağaçlarıyla nasıl çalışabileceğinize yardımcı olur. İfade ağaçlarını nasıl okuyacağınızı, ifade ağaçları oluşturmayı, değiştirilmiş ifade ağaçları oluşturmayı ve ifade ağaçları tarafından temsil edilen kodun nasıl yürütüleceğini öğreneceksiniz. Okunduktan sonra, zengin Uyarlamalı algoritmalar oluşturmak için bu yapıları kullanmaya hazırlanın.

1. [İfade Ağaçları Açıklaması](expression-trees-explained.md)

    *Ifade ağaçları*arkasındaki yapıyı ve kavramları anlayın.
    
2. [İfade Ağaçlarını Destekleyen Çerçeve Türleri](expression-classes.md)
    
    İfade ağaçlarını tanımlayan ve işleyen yapılar ve sınıflar hakkında bilgi edinin.
    
3. [İfade Yürütme](expression-trees-execution.md)

    Lambda Ifadesi olarak temsil edilen bir ifade ağacını temsilciye dönüştürmeyi ve elde edilen temsilciyi yürütmeyi öğrenin.

4. [İfade Yorumlama](expression-trees-interpreting.md)

    İfade ağacının hangi kodun temsil ettiğini anlamak için, *ifade ağaçlarına* çapraz geçiş yapma ve İnceleme hakkında bilgi edinin.

5. [İfade Derleme](expression-trees-building.md)

    Bir ifade ağacı ve derleme ifade ağaçları için düğümleri oluşturmayı öğrenin.

6. [İfade Çevirme](expression-trees-translating.md)

    Bir ifade ağacının değiştirilmiş bir kopyasını oluşturmayı veya bir ifade ağacını farklı bir biçime çevireceğinizi öğrenin.

7. [Toplam](expression-trees-summary.md)

    İfade ağaçları hakkındaki bilgileri gözden geçirin.
