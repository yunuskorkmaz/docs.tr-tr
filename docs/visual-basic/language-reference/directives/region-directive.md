---
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
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343790"
---
# <a name="region-directive"></a>#Region Yönergesi

Visual Basic dosyalardaki kod bölümlerini daraltır ve gizler.  
  
## <a name="syntax"></a>Sözdizimi  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`identifier_string`|Gerekli. Daraltılan bir bölgenin başlığı olarak davranan dize. Bölgeler varsayılan olarak daraltılır.|  
|`#End Region`|`#Region` bloğunu sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Visual Studio Code düzenleyicisinin ana hat özelliğini kullanırken genişletilecek veya daraltılacak bir kod bloğu belirtmek için `#Region` yönergesini kullanın. Benzer bölgeleri gruplamak için diğer bölgelere bölge yerleştirebilir veya *iç içe*geçirebilirsiniz.  
  
## <a name="example"></a>Örnek  

 Bu örnek `#Region` yönergesini kullanır.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
- [Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
