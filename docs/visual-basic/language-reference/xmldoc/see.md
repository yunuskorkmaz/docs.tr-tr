---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e3ae5fb63540e47e5b8da2e2d60d5bd736e019d7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524662"
---
# <a name="see-visual-basic"></a>\<see > (Visual Basic)
Başka bir üyeye bağlantı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir. `member` çift tırnak işaretleri ("") içinde yer almalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Metnin içinden bir bağlantı belirtmek için `<see>` etiketini kullanın. Bir "Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için [\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek `DoesRecordExist` yöntemine başvurmak için `UpdateRecord` açıklamaları bölümündeki `<see>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
