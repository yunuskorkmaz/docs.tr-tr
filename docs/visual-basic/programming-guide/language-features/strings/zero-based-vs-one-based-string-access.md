---
title: Sıfır Tabanlı ve Visual Basic'te bir tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591753"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Sıfır Tabanlı ve Visual Basic'te bir tabanlı dize erişimi
Bu konuda, Visual Basic ve .NET Framework bir dizedeki karakter erişimi nasıl sağladığını karşılaştırır. Visual Basic işlevi bağlı olarak, sıfır tabanlı ve bir tabanlı erişim sağlar ancak .NET Framework, her zaman bir dizedeki karakter sıfır tabanlı erişim sağlar.  
  
## <a name="one-based"></a>Bir tabanlı  
 Visual Basic bir tabanlı işlevi örneği için göz önünde bulundurun `Mid` işlevi. İşlem alt dizeyi, konum 1 ile başlayan başlayacağı karakter konumunu belirten bir bağımsız değişken alır. .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizedeki başlangıç konumu 0 ile. Bu nedenle, bir dize "ABCDE" varsa, karakterlerin tek tek ile kullanılmak üzere 1,2,3,4,5 numaralandırılır `Mid` işlevi, ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="zero-based"></a>Sıfır tabanlı  
 Sıfır tabanlı bir Visual Basic işlev örneği için göz önünde bulundurun `Split` işlevi. Bir dizeyi böler ve alt dizeler içeren bir dizi döndürür. .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi ayrıca bir dizeyi böler ve alt dizeler içeren bir dizi döndürür. Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntem .NET Framework diziler döndürür, sıfır tabanlı olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
