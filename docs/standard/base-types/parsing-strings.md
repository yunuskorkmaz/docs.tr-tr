---
title: .NET 'te dizeleri ayrıştırma
description: .NET ' te dize ayrıştırmayı anlayın. Ayrıştırma, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Ayrıştırma, biçimlendirme için ters işlemdir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769294"
---
# <a name="parsing-strings-in-net"></a>.NET 'te dizeleri ayrıştırma
Bir ayrıştırma işlemi, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Örneğin, bir dizeyi bir kayan noktalı sayıya veya tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır. Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir. Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir. Biçimlendirme <xref:System.IFormatProvider> , kültüre duyarlı biçimlendirme bilgilerini sağlamak için arabirimini uygulayan bir nesne kullandığından, ayrıştırma aynı zamanda <xref:System.IFormatProvider> bir dize gösterimini nasıl yorumlayacağını belirleme arabirimini uygulayan bir nesne kullanır. Daha fazla bilgi için bkz. [Biçimlendirme Türleri](formatting-types.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sayısal Dizeleri Ayrıştırma](parsing-numeric.md)  
 Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.  
  
 [Tarih ve Saat Dizelerini Ayrıştırma](parsing-datetime.md)  
 Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.  
  
 [Diğer Dizeleri Ayrıştırma](parsing-other.md)  
 Dizelerin **char**, **Boolean**ve **enum** türlerine nasıl dönüştürüleceğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Biçimlendirme Türleri](formatting-types.md)  
 Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.  
  
 [.NET 'te tür dönüştürme](type-conversion.md)  
 Türlerin nasıl dönüştürüleceğini açıklar.
