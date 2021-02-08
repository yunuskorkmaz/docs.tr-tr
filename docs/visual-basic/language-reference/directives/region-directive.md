---
description: 'Daha fazla bilgi edinin: #Region yönergesi'
title: '#Region Yönergesi'
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
ms.openlocfilehash: 4ba1645cfc51a69d39e6a60b5ea236dd65883e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797230"
---
# <a name="region-directive"></a>#Region Yönergesi

Visual Basic dosyalardaki kod bölümlerini daraltır ve gizler.  
  
## <a name="syntax"></a>Syntax  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Bölümler  
  
|Süre|Tanım|  
|---|---|  
|`identifier_string`|Gereklidir. Daraltılan bir bölgenin başlığı olarak davranan dize. Bölgeler varsayılan olarak daraltılır.|  
|`#End Region`|Bloğu sonlandırır `#Region` .|  
  
## <a name="remarks"></a>Açıklamalar  

 `#Region`Visual Studio Code düzenleyicisinin ana hat özelliğini kullanırken genişletilecek veya daraltılacak bir kod bloğu belirtmek için yönergesini kullanın. Benzer bölgeleri gruplamak için diğer bölgelere bölge yerleştirebilir veya *iç içe* geçirebilirsiniz.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `#Region` yönergesini kullanır.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [#If... Sonra... #Else yönergeler](if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
- [Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
