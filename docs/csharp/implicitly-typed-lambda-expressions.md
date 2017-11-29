---
title: "Türü örtük olarak belirlenmiş lambda ifadeleri"
description: "Lambda ifadesi bildirmek için örtük olarak yazılan bir değişken bildirimi neden kullanamazsınız öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 663613af001f9727c48bd48553540305e47a6bab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implicitly-typed-lambda-expressions"></a>Türü örtük olarak belirlenmiş lambda ifadeleri

Değil kullanıyorum `var` Bu ifade ağacına bildirmek için. Türü örtük olarak belirlenmiş bir değişken bildirimi lambda ifadesi bildirmek için kullanamazsınız.
Derleyici için döngüsel mantığı sorun oluşturur. `var` Bildirimi atama işlecinin sağ tarafında ifadenin türünden değişkeninin türü ekleneceğini derleyici söyler. Lambda ifadesi bir derleme zamanı türüne sahip değil, ancak hiçbir eşleşen temsilci ya da ifade türüne dönüştürülemez. Lambda ifadesi bir temsilci ya da ifade türü bir değişkene atadığınızda, deneyin ve lambda ifadesi bir deyim veya 'atanan' değişkeni imzası eşleşen temsilci dönüştürmek için derleyici söyleyin. Derleyici sağ tarafta atama eşleşme türünü sol taraftaki atama şey yapmaya gerekir. 

Atama her iki tarafında derleyici atama işleci diğer tarafta nesneye bakabilir ve my türü eşleşip eşleşmediğini belirten olamaz.

Neden bu davranışı belirtir okuyarak C# dili hakkında daha fazla bilgi alabilirsiniz [bu makalede](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF indirin)


