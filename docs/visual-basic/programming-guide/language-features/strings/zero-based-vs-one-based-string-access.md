---
title: Sıfır tabanlı ve tek tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: ce2fcb2610c09a9591a5fd79da4baa74cc533c99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363662"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Visual Basic'de Sıfır Tabanlı ve Bir Tabanlı Dize Erişimi
Bu konu, Visual Basic ve .NET Framework bir dizedeki karakterlere erişim sağlama şeklini karşılaştırır. .NET Framework her zaman bir dizedeki karakterlere sıfır tabanlı erişim sağlar, ancak Visual Basic, işleve bağlı olarak sıfır tabanlı ve tek tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Tek tabanlı  
 Tek tabanlı Visual Basic işlevinin bir örneği için, işlevi göz önünde bulundurun `Mid` . 1. konumdan başlayarak alt dizenin başlayacağı karakter konumunu gösteren bir bağımsız değişken alır. .NET Framework yöntemi, alt <xref:System.String.Substring%2A?displayProperty=nameWithType> dizenin başlatılacağı dizedeki karakterin bir dizinini alır. konum 0 ' dan başlar. Bu nedenle, "ABCDE" dizeniz varsa, tek tek karakterler 1, 2, 3, 4, işleviyle kullanım için 5, `Mid` 1, 2, 3, 4, yöntemiyle birlikte kullanılmak üzere numaralandırılır <xref:System.String.Substring%2A?displayProperty=nameWithType> .  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Sıfır tabanlı Visual Basic işlevinin bir örneği için, işlevi göz önünde bulundurun `Split` . Bir dizeyi böler ve alt dizeleri içeren bir dizi döndürür. .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi bir dizeyi de böler ve alt dizeleri içeren bir dizi döndürür. `Split`İşlev ve <xref:System.String.Split%2A> Yöntem .NET Framework diziler döndürdüğü için, bunların sıfır tabanlı olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
