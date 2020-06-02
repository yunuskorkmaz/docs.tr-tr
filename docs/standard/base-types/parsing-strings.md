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
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277420"
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
