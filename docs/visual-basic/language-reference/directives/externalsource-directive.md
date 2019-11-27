---
title: '#ExternalSource Yönergesi'
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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343825"
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
 `#ExternalSource` bloğunu sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yönerge yalnızca derleyici ve hata ayıklayıcı tarafından kullanılır.  
  
 Kaynak dosya, kaynak dosyadaki belirli kod satırları ve bir. aspx dosyası gibi, kaynağın harici metni arasındaki eşlemeyi gösteren dış kaynak yönergeleri içerebilir. Derleme sırasında belirlenen kaynak kodunda hatalarla karşılaşılırsa, bunlar dış kaynaktan geldiği şekilde tanımlanır.  
  
 Dış kaynak yönergelerinin derleme üzerinde hiçbir etkisi yoktur ve iç içe geçirilemez. Bunlar yalnızca uygulama tarafından dahili kullanım için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
