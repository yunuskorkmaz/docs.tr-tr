---
title: . NET'te dizeleri ayrıştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766005"
---
# <a name="parsing-strings-in-net"></a>. NET'te dizeleri ayrıştırma
Bir ayrıştırma işlemi, temel türü .NET taban türünü temsil eden bir dizeye dönüştürür. Örneğin, bir ayrıştırma işlemi, bir dizeyi bir kayan noktalı sayı veya tarih ve saat değerini dönüştürmek için kullanılır. Bir ayrıştırma işlemi gerçekleştirmek için en yaygın kullanılan yöntemdir `Parse` yöntemi. Ayrıştırma (Bu bir taban türü dize gösterimine dönüştürme içerir) biçimlendirme tersine çevirme işlemi olduğundan, çoğu aynı kuralları ve kuralları geçerlidir. Yalnızca biçimlendirme olarak uygulayan bir nesne kullanır <xref:System.IFormatProvider> arabirimi uygulayan bir nesne de kullandığı ayrıştırma kültüre duyarlı biçimlendirme bilgilerini sağlamak üzere <xref:System.IFormatProvider> dize gösterimini yorumlama belirlemek için arabirimi . Daha fazla bilgi için [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)  
 Dizeleri .NET sayısal türlerine dönüştüren açıklar.  
  
 [Tarih ve Saat Dizelerini Ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)  
 .NET Framework'e dizeleri dönüştürüleceğini açıklar **DateTime** türleri.  
  
 [Diğer Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-other.md)  
 Dizelere dönüştürülebileceği açıklar **Char**, **Boole**, ve **Enum** türleri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 Biçim belirticileri ve biçim sağlayıcıları gibi biçimlendirme temel kavramları açıklar.  
  
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)  
 Türleri dönüştürme işlemini açıklamaktadır.  
  
 [Temel Türler](../../../docs/standard/base-types/index.md)  
 .NET temel türleri üzerinde gerçekleştirebileceğiniz sık kullanılan işlemleri açıklar.
