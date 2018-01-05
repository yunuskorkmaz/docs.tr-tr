---
title: ".NET dizeleri ayrıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9c2193dd1b1f3c0478efb5fc9c2b80250ef1878f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-strings-in-net"></a>.NET dizeleri ayrıştırma
Ayrıştırma işlemi bir .NET taban türü, temel türü içine temsil eden bir dize dönüştürür. Örneğin, bir ayrıştırma işlemi, bir dizeyi bir kayan noktalı sayı veya tarih ve saat değerine dönüştürmek için kullanılır. Ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntemidir `Parse` yöntemi. Ayrıştırma (bir taban türü dize gösterimine dönüştürülmesi içerir) biçimlendirme tersine çevirme işlemi olduğundan, aynı kuralları ve kuralları birçoğu uygulayın. Arabirimini uygulayan bir nesneye yalnızca biçimlendirme olarak kullanan <xref:System.IFormatProvider> arabirimini uygulayan bir nesne de kullandığı ayrıştırma kültüre duyarlı biçimlendirme bilgi sağlamak için <xref:System.IFormatProvider> bir dize gösterimi yorumlama belirlemek için arabirimi . Daha fazla bilgi için bkz: [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)  
 Dizeleri .NET sayısal türlerine dönüştürmek açıklar.  
  
 [Tarih ve Saat Dizelerini Ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)  
 Dizeleri .NET dönüştürülmesi açıklanmaktadır **DateTime** türleri.  
  
 [Diğer Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-other.md)  
 Dizelere dönüştürme açıklar **Char**, **Boolean**, ve **Enum** türleri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 Biçim belirticiler ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.  
  
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)  
 Türleri dönüştürme açıklar.  
  
 [Temel Türler](../../../docs/standard/base-types/index.md)  
 .NET temel türlerinde gerçekleştirdiğiniz ortak işlemleri açıklanır.
