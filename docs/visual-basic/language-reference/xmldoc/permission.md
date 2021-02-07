---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <permission> (Visual Basic)'
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 7a227e97051002c834c96297d3028f08e3ed07ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700266"
---
# <a name="permission-visual-basic"></a>\<permission> (Visual Basic)

Üye için gerekli izinleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
