---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0231ff748949874f4b477cac15d891d313b25f4f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524652"
---
# <a name="seealso-visual-basic"></a>\<seealso > (Visual Basic)
Ayrıca bkz. bölümünde görüntülenen bir bağlantı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir. `member` çift tırnak işaretleri ("") içinde yer almalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtmek için `<seealso>` etiketini kullanın. Metnin içinden bir bağlantı belirtmek için [\<see >](../../../visual-basic/language-reference/xmldoc/see.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek `UpdateRecord` yöntemine başvurmak için `DoesRecordExist` açıklamaları bölümündeki `<seealso>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
