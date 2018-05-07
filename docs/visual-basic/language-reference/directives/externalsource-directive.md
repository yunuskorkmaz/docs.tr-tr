---
title: '#ExternalSource yönergesi'
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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="externalsource-directive"></a>#ExternalSource Yönergesi
Belirli satırları kaynak kodu ve metin kaynağına dış arasında bir eşleme gösterir.  
  
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
 Dış kaynak ilk satırının satır sayısı.  
  
 `LogicalLine`  
 Dış kaynak hatanın oluştuğu satır.  
  
 `#End ExternalSource`  
 Sonlandırır `#ExternalSource` bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yönerge, yalnızca derleme ve hata ayıklayıcısı tarafından kullanılır.  
  
 Bir kaynak dosyası belirli satırları kaynak dosyasında kod ve metin kaynağına .aspx dosyası gibi dış arasında bir eşleme belirtmek dış kaynak yönergeleri içerir. Belirtilen kaynak kodunda derleme sırasında bir hatayla karşılaşılmazsa, dış kaynak gelen olarak tanımlanır.  
  
 Dış kaynak yönergeleri derleme üzerinde hiçbir etkisi yoktur ve iç içe olamaz. Yalnızca uygulama tarafından bunlar iç kullanım için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
