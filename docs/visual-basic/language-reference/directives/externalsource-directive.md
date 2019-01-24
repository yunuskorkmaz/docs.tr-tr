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
ms.openlocfilehash: 550934723a5599573be578ce5746ab7520b59dd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705975"
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
