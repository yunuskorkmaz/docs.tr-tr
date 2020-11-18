---
title: Dizeleri türlere Dönüştür
description: .NET ' te dize ayrıştırmayı anlayın. Ayrıştırma, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Ayrıştırma, biçimlendirme için ters işlemdir.
ms.date: 03/30/2017
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 8fbfe8596e49ed101ea7d6bb65298e432a6fac13
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821911"
---
# <a name="parse-strings-in-net"></a>.NET 'teki dizeleri ayrıştırma

Bir *ayrıştırma* işlemi, .net temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Örneğin, bir dizeyi bir kayan noktalı sayıya veya bir tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır. Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir. Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir. Biçimlendirme <xref:System.IFormatProvider> , kültüre duyarlı biçimlendirme bilgilerini sağlamak için arabirimini uygulayan bir nesne kullandığından, ayrıştırma aynı zamanda <xref:System.IFormatProvider> bir dize gösterimini nasıl yorumlayacağını belirleme arabirimini uygulayan bir nesne kullanır. Daha fazla bilgi için bkz. [Biçim türleri](formatting-types.md).

## <a name="in-this-section"></a>Bu Bölümde
 [Sayısal dizeleri ayrıştırma](parsing-numeric.md)\
 Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.

 [Tarih ve saat dizelerini ayrıştırma](parsing-datetime.md)\
 Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.

 [Diğer dizeleri ayrıştırma](parsing-other.md)\
 Dizelerin **char**, **Boolean** ve **enum** türlerine nasıl dönüştürüleceğini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [Biçimlendirme türleri](formatting-types.md)\
 Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.

 [.NET 'te tür dönüştürme](type-conversion.md)\
 Türlerin nasıl dönüştürüleceğini açıklar.
