---
title: '#Bölge yönergesi'
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
ms.openlocfilehash: d25871140ef0674c013fc70d1306b2b4d0858556
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="region-directive"></a>#Region Yönergesi
Daraltır ve Visual Basic dosyaları kodda bölümlerini gizler.  
  
## <a name="syntax"></a>Sözdizimi  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`identifier_string`|Gerekli. Daraltılmış durumda olduğunda, bir bölge başlığı olarak davranan dizesi. Bölgeleri varsayılan olarak daraltılır.|  
|`#End Region`|Sonlandırır `#Region` bloğu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `#Region` yönergesi genişletmek veya Visual Studio Kod Düzenleyicisi'nin anahat özelliğini kullanırken daraltmak için kod bloğunu belirtin. Koyabilirsiniz, veya *iç içe*, bölge benzer bölgeler gruplamak için diğer bölge içinde.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `#Region` yönergesi.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Anahat Oluşturma](/visualstudio/ide/outlining)  
 [Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
