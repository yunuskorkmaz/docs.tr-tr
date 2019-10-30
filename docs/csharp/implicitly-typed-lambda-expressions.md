---
title: Örtük olarak yazılan lambda ifadeleri
description: Bir lambda ifadesi bildirmek için neden örtük olarak yazılmış bir değişken bildirimi kullanamadığınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: c6b0f2666a5c67ce8c89222da5959304ecb8fb93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039136"
---
# <a name="implicitly-typed-lambda-expressions"></a>Örtük olarak yazılan lambda ifadeleri

Bir lambda ifadesi bildirmek için örtük olarak yazılmış bir değişken bildirimi kullanamazsınız.
Derleyici için bir dairesel mantık sorunu oluşturur. `var` bildirimi, derleyiciye atama işlecinin sağ tarafındaki ifadenin türünden değişkenin türünü eklemesini söyler. Lambda ifadesinin derleme zamanı türü yoktur, ancak eşleşen herhangi bir temsilciye veya ifade türüne dönüştürülebilir. Bir temsilci veya ifade türü değişkenine bir lambda ifadesi atadığınızda, derleyiciye lambda ifadesini ' atandı ' değişkeninin imzasıyla eşleşen bir ifadeye veya temsilciye dönüştürmenize söylemiş olursunuz. Derleyicinin, atamanın sağ tarafındaki her şeyi atamanın sol tarafındaki türle eşleştirmek için deneme yapması gerekir. 

Atamanın her iki tarafı da derleyiciye atama işlecinin diğer tarafındaki nesneye bakmasını ve bu türden eşleşip eşleşmediğini görmenizi söyleyemiyorum.

C# [Bu makaleyi](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) okuyarak dilin neden bu davranışı belirtmekle ilgili daha fazla ayrıntı alabilirsiniz (PDF indirme)
