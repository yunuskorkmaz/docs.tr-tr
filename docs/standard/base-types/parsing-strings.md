---
title: .NET 'te dizeleri ayrıştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084309"
---
# <a name="parsing-strings-in-net"></a>.NET 'te dizeleri ayrıştırma
Bir ayrıştırma işlemi, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Örneğin, bir dizeyi bir kayan noktalı sayıya veya tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır. Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir. Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir. Biçimlendirme, kültüre duyarlı biçimlendirme bilgilerini sağlamak için <xref:System.IFormatProvider> arabirimini uygulayan bir nesne kullandığından, ayrıştırma Ayrıca bir dize gösterimini nasıl yorumlayacağını anlamak için <xref:System.IFormatProvider> arabirimini uygulayan bir nesne kullanır. Daha fazla bilgi için bkz. [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)  
 Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.  
  
 [Tarih ve Saat Dizelerini Ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)  
 Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.  
  
 [Diğer Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-other.md)  
 Dizelerin **char**, **Boolean**ve **enum** türlerine nasıl dönüştürüleceğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.  
  
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)  
 Türlerin nasıl dönüştürüleceğini açıklar.  
  
 [Temel Türler](../../../docs/standard/base-types/index.md)  
 .NET temel türlerinde gerçekleştirebileceğiniz yaygın işlemleri açıklar.
