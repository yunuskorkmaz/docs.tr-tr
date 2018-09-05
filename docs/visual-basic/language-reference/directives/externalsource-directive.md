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
ms.openlocfilehash: dcde8507eb033d0a47d5c5d3fa36176cd63b0856
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556324"
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
