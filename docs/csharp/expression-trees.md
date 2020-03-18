---
title: İfade Ağaçları
description: .NET Core'daki ifade ağaçları ve kodu inceleyebilir, değiştirebileceğiniz ve yürütebileceğiniz yapılar olarak ifade etmek için bunları nasıl kullanacağınız hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145845"
---
# <a name="expression-trees"></a>İfade Ağaçları

LINQ kullandıysanız, türlerin API kümesinin `Func` bir parçası olduğu zengin bir kitaplık la deneyiminiz vardır. (EĞER LINQ aşina değilseniz, muhtemelen bundan önce [LINQ öğretici](linq/index.md) ve [lambda ifadeler](./programming-guide/statements-expressions-operators/lambda-expressions.md) hakkında makale okumak istiyorum.) *İfade Ağaçlar* işlevleri olan bağımsız değişkenler ile daha zengin etkileşim sağlar.

LINQ sorguları oluştururken genellikle Lambda İfadeleri'ni kullanarak işlev bağımsız değişkenleri yazarsınız. Tipik bir LINQ sorgusunda, bu işlev bağımsız değişkenleri derleyicinin oluşturduğu bir temsilciye dönüştürülür.

Daha zengin bir etkileşim esahip olmak istediğinizde, *İfade Ağaçları*kullanmanız gerekir.
İfade Ağaçları kodu inceleyebilir, değiştirebileceğiniz veya yürütebileceğiniz bir yapı olarak temsil ederler. Bu araçlar, çalışma süresi boyunca kodu işleme gücü verir. Çalışan algoritmaları inceleyen veya yeni özellikler enjekte eden kod yazabilirsiniz. Daha gelişmiş senaryolarda, çalışan algoritmaları değiştirebilir ve hatta C# ifadelerini başka bir ortamda yürütme için başka bir forma çevirebilirsiniz.

Büyük olasılıkla İfade Ağaçları kullanan kod yazdınız. Entity Framework'ün LINQ API'leri, Linq Sorgu İfade Deseni'nin bağımsız değişkenleri olarak İfade Ağaçları'nı kabul eder.
Bu, [Entity Framework'ün](/ef/) C#'da yazdığınız sorguyu veritabanı altyapısında yürüten SQL'e çevirmesini sağlar. Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir alay çerçevesidir.

Bu öğreticinin kalan bölümleri, İfade Ağaçlarının ne olduğunu inceleyecek, ifade ağaçlarını destekleyen çerçeve sınıflarını inceleyecek ve ifade ağaçlarıyla nasıl çalışacağınızı gösterecektir. İfade ağaçlarını okumayı, ifade ağaçlarının nasıl oluşturulacağını, değiştirilmiş ifade ağaçlarının nasıl oluşturulacağını ve ifade ağaçlarıyla temsil edilen kodun nasıl yürütüleceğini öğreneceksiniz. Okuduktan sonra, zengin uyarlanabilir algoritmalar oluşturmak için bu yapıları kullanmaya hazır olacak.

1. [İfade Ağaçları Açıklaması](expression-trees-explained.md)

    *İfade Ağaçlarının*arkasındaki yapı ve kavramları anlayın.

2. [İfade Ağaçlarını Destekleyen Çerçeve Türleri](expression-classes.md)

    İfade ağaçlarını tanımlayan ve manipüle eden yapılar ve sınıflar hakkında bilgi edinin.

3. [İfade Yürütme](expression-trees-execution.md)

    Lambda İfadesi olarak temsil edilen bir ifade ağacını temsilciye nasıl dönüştüreceklerini ve elde edilen temsilciyi nasıl yürütüldüğünü öğrenin.

4. [İfade Yorumlama](expression-trees-interpreting.md)

    İfade ağacının hangi kodu temsil etmesini anlamak için *ifade ağaçlarını* nasıl inceleyeceğinizi ve inceleyeceğinizi öğrenin.

5. [İfade Derleme](expression-trees-building.md)

    İfade ağacı için düğümleri nasıl oluşturup ifade ağaçları inşa etmeyi öğrenin.

6. [İfade Çevirme](expression-trees-translating.md)

    İfade ağacının değiştirilmiş bir kopyasını nasıl oluşturarak nasıl çevireceklerini veya bir ifade ağacını farklı bir biçime nasıl çevireceklerini öğrenin.

7. [Özetleme](expression-trees-summary.md)

    İfade ağaçlarıyla ilgili bilgileri gözden geçirin.
