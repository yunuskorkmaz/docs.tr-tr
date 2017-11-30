---
title: "#<a name=\"region-directive\"></a>Bölge yönergesi"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb308da6ad0ca6243f14e0d825ed7eb005d622bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="region-directive"></a>#Region Yönergesi
Daraltır ve Visual Basic dosyaları kodda bölümlerini gizler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Anahat oluşturma](/visualstudio/ide/outlining)  
 [Nasıl yapılır: daraltma ve gizleme kodun bölümlerini](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
