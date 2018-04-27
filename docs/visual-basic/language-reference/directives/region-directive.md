---
title: '#Bölge yönergesi'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83ceac7d73eff23e16c5f6efb1c4eb8a2210ee2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
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
