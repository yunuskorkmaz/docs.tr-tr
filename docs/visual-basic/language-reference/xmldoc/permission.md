---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: b3acec04060367a0b9e54b19c0106644d028357b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400040"
---
# <a name="permission-visual-basic"></a>\<permission> (Visual Basic)
Üye için gerekli izinleri belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında kurallı öğe adına çevirir. `member`Tırnak işaretleri ("") içine alın.  
  
 `description`  
 Üyeye erişim açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 `<permission>`Bir üyenin erişimini belgelemek için etiketini kullanın. <xref:System.Security.PermissionSet>Bir üyeye erişimi belirtmek için sınıfını kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `<permission>` yöntemi için gerekli olduğunu betimleyen etiketini kullanır <xref:System.Security.Permissions.FileIOPermission> `ReadFile` .  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
