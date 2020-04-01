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
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523811"
---
# <a name="parsing-strings-in-net"></a>.NET'te Dizeleri Ayrışdırma
Ayrıştma işlemi, .NET taban türünü temsil eden bir dizeyi bu taban türüne dönüştürür. Örneğin, bir ayrıştırma işlemi, bir dizeyi kayan nokta numarasına veya tarih ve saat değerine dönüştürmek için kullanılır. Ayrıştırma işlemini gerçekleştirmek için en sık `Parse` kullanılan yöntem yöntemdir. Ayrıştırma biçimlendirmenin ters işlemi olduğundan (bir taban türünü dize gösterimine dönüştürmeyi içerir), aynı kural ve kuralların çoğu geçerlidir. Biçimlendirme, kültüre duyarlı biçimlendirme <xref:System.IFormatProvider> bilgileri sağlamak için arabirimi uygulayan bir nesne kullandığı gibi, <xref:System.IFormatProvider> ayrıştırma da dize gösterimini nasıl yorumlayacaklarını belirlemek için arabirimi uygulayan bir nesne kullanır. Daha fazla bilgi için bkz. [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)  
 Dizeleri .NET sayısal türlerine nasıl dönüştüreceklerini açıklar.  
  
 [Tarih ve Saat Dizelerini Ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)  
 Dizeleri .NET **DateTime** türlerine nasıl dönüştüreceklerini açıklar.  
  
 [Diğer Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-other.md)  
 Dizeleri **Char,** **Boolean**ve **Enum** türlerine nasıl dönüştüreceklerini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 Biçim belirteciler ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.  
  
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)  
 Türlerin nasıl dönüştürülür şekilde dönüştürülür açıklanır.
