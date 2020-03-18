---
title: Örtülü olarak yazılan lambda ifadeleri
description: Lambda ifadesini bildirmek için neden örtülü olarak yazılan değişken bildirimi ni yazamayacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145728"
---
# <a name="implicitly-typed-lambda-expressions"></a>Örtülü olarak yazılan lambda ifadeleri

Lambda ifadesini bildirmek için örtülü olarak yazılan değişken bildirimi kullanamazsınız.
Derleyici için dairesel bir mantık sorunu oluşturur. Bildirim, `var` derleyiciye atama işlecinin sağ tarafındaki ifade türünden değişkenin türünü belirlemesini söyler. Lambda ifadesi derleme zaman türüne sahip değildir, ancak eşleşen herhangi bir temsilci veya ifade türüne dönüştürülebilir. Bir temsilci veya ifade türü değişkenine lambda ifadesini atadığınızda, derleyiciye lambda ifadesini 'atanan' değişkenin imzasına uyan bir ifadeye veya temsilciye dönüştürmeyi denemesini söylersiniz. Derleyici, atamanın sağ tarafındaki şeyi atamanın sol tarafındaki türle eşleştirmeye çalışmalıdır.

Atamanın her iki tarafı da derleyiciye atama işlecinin diğer tarafındaki nesneye bakmasını ve türümün türümün eşleşip eşleşmeyeceğini görmesini söyleyemez.

C# dilinin bu davranışı neden belirttiği hakkında daha fazla bilgi bu [makaleyi](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) okuyarak (PDF indir) alabilirsiniz.
