---
title: .NET'te Dizeleri Ayrışdırma
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084309"
---
# <a name="parsing-strings-in-net"></a>.NET'te Dizeleri Ayrışdırma
Ayrıştma işlemi, .NET taban türünü temsil eden bir dizeyi bu taban türüne dönüştürür. Örneğin, bir ayrıştırma işlemi, bir dizeyi kayan nokta numarasına veya tarih ve saat değerine dönüştürmek için kullanılır. Ayrıştırma işlemini gerçekleştirmek için en sık `Parse` kullanılan yöntem yöntemdir. Ayrıştırma biçimlendirmenin ters işlemi olduğundan (bir taban türünü dize gösterimine dönüştürmeyi içerir), aynı kural ve kuralların çoğu geçerlidir. Biçimlendirme, kültüre duyarlı biçimlendirme <xref:System.IFormatProvider> bilgileri sağlamak için arabirimi uygulayan bir nesne kullandığı gibi, <xref:System.IFormatProvider> ayrıştırma da dize gösterimini nasıl yorumlayacaklarını belirlemek için arabirimi uygulayan bir nesne kullanır. Daha fazla bilgi için bkz. [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sayısal Dizeleri Ayrıştma](../../../docs/standard/base-types/parsing-numeric.md)  
 Dizeleri .NET sayısal türlerine nasıl dönüştüreceklerini açıklar.  
  
 [Tarih ve Saat Dizelerini Ayrışdırma](../../../docs/standard/base-types/parsing-datetime.md)  
 Dizeleri .NET **DateTime** türlerine nasıl dönüştüreceklerini açıklar.  
  
 [Diğer Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-other.md)  
 Dizeleri **Char,** **Boolean**ve **Enum** türlerine nasıl dönüştüreceklerini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 Biçim belirteciler ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.  
  
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)  
 Türlerin nasıl dönüştürülür şekilde dönüştürülür açıklanır.  
  
 [Temel Türler](../../../docs/standard/base-types/index.md)  
 .NET taban türlerinde gerçekleştirebileceğiniz yaygın işlemleri açıklar.
