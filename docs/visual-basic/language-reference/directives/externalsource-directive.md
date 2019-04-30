---
title: '#ExternalSource yönergesi (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747050"
---
# <a name="externalsource-directive"></a>#ExternalSource Yönergesi
Belirli bir kaynak kodu satırlarını ve dış kaynak metin arasındaki eşlemeyi gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Bölümler  
 `StringLiteral`  
 Dış kaynak yolu.  
  
 `IntLiteral`  
 Dış kaynağı ilk satırının satır sayısı.  
  
 `LogicalLine`  
 Dış kaynağında hatanın oluştuğu satırı.  
  
 `#End ExternalSource`  
 Sonlandırır `#ExternalSource` blok.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yönerge, yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.  
  
 Kaynak dosyada kodun belirli satırlarını ve dış .aspx dosyası gibi bir kaynak metin arasındaki eşlemeyi belirtmek dış kaynak yönergelerini, bir kaynak dosyası içerebilir. Belirtilen kaynak kodunda derleme sırasında bir hatayla karşılaşılmazsa, bir dış kaynaktan gelen olarak tanımlanır.  
  
 Dış kaynak yönergeleri derleme üzerinde hiçbir etkisi yoktur ve iç içe olamaz. Bunlar yalnızca uygulama tarafından iç kullanım için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
