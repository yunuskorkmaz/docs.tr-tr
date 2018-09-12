---
title: '#Bölge yönergesi (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 204b53751fce4f9a3e038ae7c44634522d54657c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707522"
---
# <a name="region-directive"></a>#Region Yönergesi
Daraltır ve Visual Basic dosyalarında kod bölümlerini gizler.  
  
## <a name="syntax"></a>Sözdizimi  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`identifier_string`|Gerekli. Bunu daraltıldığında bir bölge başlığı olarak davranan dize. Bölgeleri varsayılan olarak daraltılır.|  
|`#End Region`|Sonlandırır `#Region` blok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `#Region` genişletmek veya daraltmak için anahat oluşturma özelliği Visual Studio Kod Düzenleyicisi'nin kullanırken kod bloğu belirtmek için. Yerleştirebilirsiniz veya *iç içe*, benzer bölgeleri gruplamak için başka bölgelerde bulunan bölge.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `#Region` yönergesi.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Anahat Oluşturma](/visualstudio/ide/outlining)  
 [Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
