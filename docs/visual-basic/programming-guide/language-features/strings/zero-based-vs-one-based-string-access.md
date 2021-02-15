---
description: "Hakkında daha fazla bilgi edinin: Visual Basic 'de sıfır tabanlı ve tek tabanlı dize erişimi"
title: Sıfır tabanlı ve tek tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: adab6954c4329ae0a547d136f26f6c3115dc5890
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463838"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Visual Basic'de Sıfır Tabanlı ve Bir Tabanlı Dize Erişimi

Bu konu, Visual Basic ve .NET Framework bir dizedeki karakterlere erişim sağlama şeklini karşılaştırır. .NET Framework her zaman bir dizedeki karakterlere sıfır tabanlı erişim sağlar, ancak Visual Basic, işleve bağlı olarak sıfır tabanlı ve tek tabanlı erişim sağlar.  
  
## <a name="one-based"></a>One-Based  

 Tek tabanlı Visual Basic işlevinin bir örneği için, işlevi göz önünde bulundurun `Mid` . 1. konumdan başlayarak alt dizenin başlayacağı karakter konumunu gösteren bir bağımsız değişken alır. .NET Framework yöntemi, alt <xref:System.String.Substring%2A?displayProperty=nameWithType> dizenin başlatılacağı dizedeki karakterin bir dizinini alır. konum 0 ' dan başlar. Bu nedenle, "ABCDE" dizeniz varsa, tek tek karakterler 1, 2, 3, 4, işleviyle kullanım için 5, `Mid` 1, 2, 3, 4, yöntemiyle birlikte kullanılmak üzere numaralandırılır <xref:System.String.Substring%2A?displayProperty=nameWithType> .  
  
## <a name="zero-based"></a>Zero-Based  

 Sıfır tabanlı Visual Basic işlevinin bir örneği için, işlevi göz önünde bulundurun `Split` . Bir dizeyi böler ve alt dizeleri içeren bir dizi döndürür. .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi bir dizeyi de böler ve alt dizeleri içeren bir dizi döndürür. `Split`İşlev ve <xref:System.String.Split%2A> Yöntem .NET Framework diziler döndürdüğü için, bunların sıfır tabanlı olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
