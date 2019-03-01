---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: c0f1293fa0161a9a11b4e80301f5c4c4ddffe7b1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969303"
---
# <a name="see-visual-basic"></a>\<bkz: > (Visual Basic)
Başka bir üyesine bir bağlantı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `member`  
 Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru. Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı. `member` çift tırnak içinde yer almalıdır ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<see>` bağlantı metninde belirtmek için etiket. Kullanım [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) "bir Ayrıca bkz:" bölümünde görünmesini istediğiniz metni belirtmek için.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<see>` içindeki `UpdateRecord` başvurmak için bölüm açıklamalar `DoesRecordExist` yöntemi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
