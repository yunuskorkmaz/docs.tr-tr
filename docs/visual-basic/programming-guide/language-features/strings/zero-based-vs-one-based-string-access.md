---
title: Sıfır tabanlı ve tek tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354294"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Visual Basic'de Sıfır Tabanlı ve Bir Tabanlı Dize Erişimi
Bu konu, Visual Basic ve .NET Framework bir dizedeki karakterlere erişim sağlama şeklini karşılaştırır. .NET Framework her zaman bir dizedeki karakterlere sıfır tabanlı erişim sağlar, ancak Visual Basic, işleve bağlı olarak sıfır tabanlı ve tek tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Tek tabanlı  
 Tek tabanlı Visual Basic işlevinin bir örneği için `Mid` işlevini göz önünde bulundurun. 1\. konumdan başlayarak alt dizenin başlayacağı karakter konumunu gösteren bir bağımsız değişken alır. .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi, alt dizenin başlatılacağı dizedeki karakterin bir dizinini alır. konum 0 ' dan başlar. Bu nedenle, "ABCDE" dizeniz varsa, tek tek karakterler `Mid` işlevi ile birlikte kullanılmak üzere 1, 2, 3, 4, 5 ve <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemiyle birlikte kullanılmak üzere 0, 1, 2, 3, 4 olarak numaralandırılır.  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Sıfır tabanlı Visual Basic işlevinin bir örneği için `Split` işlevini göz önünde bulundurun. Bir dizeyi böler ve alt dizeleri içeren bir dizi döndürür. .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi bir dizeyi de böler ve alt dizeleri içeren bir dizi döndürür. `Split` işlevi ve <xref:System.String.Split%2A> yöntemi .NET Framework dizileri döndürtiğinden, bunların sıfır tabanlı olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
