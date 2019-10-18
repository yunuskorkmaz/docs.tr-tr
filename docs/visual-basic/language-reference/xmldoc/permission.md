---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524692"
---
# <a name="permission-visual-basic"></a>\<permission > (Visual Basic)
Üye için gerekli izinleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir. @No__t_0 tırnak işaretleri ("") içine alın.  
  
 `description`  
 Üyeye erişim açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 Üyenin erişimini belgelemek için `<permission>` etiketini kullanın. Bir üyeye erişimi belirtmek için <xref:System.Security.PermissionSet> sınıfını kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `ReadFile` yöntemi tarafından <xref:System.Security.Permissions.FileIOPermission> gerektiğini belirtmek için `<permission>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
