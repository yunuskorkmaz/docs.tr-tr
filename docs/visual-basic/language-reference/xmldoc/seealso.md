---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 9f857be6d0bd46233a49c7d2ff0931670baa95a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965312"
---
# <a name="seealso-visual-basic"></a>\<SeeAlso > (Visual Basic)
Ayrıca bkz. bölümünde görünen bağlantıyı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `member`  
 Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru. Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı. `member` çift tırnak içinde yer almalıdır ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<seealso>` ayrıca bölümü görünmesini istediğiniz metni belirtmek için etiket. Kullanım [ \<bakın >](../../../visual-basic/language-reference/xmldoc/see.md) bağlantı metninde belirtmek için.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<seealso>` içindeki `DoesRecordExist` başvurmak için bölüm açıklamalar `UpdateRecord` yöntemi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
