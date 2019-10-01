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
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696833"
---
# <a name="externalsource-directive"></a>#ExternalSource Yönergesi
Kaynak kodunun belirli satırları ve kaynağın dış metni arasındaki eşlemeyi gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Bölümler  
 `StringLiteral`  
 Dış kaynağın yolu.  
  
 `IntLiteral`  
 Dış kaynağın ilk satırının satır numarası.  
  
 `LogicalLine`  
 Dış kaynakta Hatanın gerçekleştiği satır.  
  
 `#End ExternalSource`  
 @No__t-0 bloğunu sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yönerge yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.  
  
 Kaynak dosya, kaynak dosyadaki belirli kod satırları ve bir. aspx dosyası gibi, kaynağın harici metni arasındaki eşlemeyi gösteren dış kaynak yönergeleri içerebilir. Derleme sırasında belirlenen kaynak kodunda hatalarla karşılaşılırsa, bunlar dış kaynaktan geldiği şekilde tanımlanır.  
  
 Dış kaynak yönergelerinin derleme üzerinde hiçbir etkisi yoktur ve iç içe geçirilemez. Bunlar yalnızca uygulama tarafından dahili kullanım için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
