---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: a8914e6d8fbce3e99ff92d9e4968e85a0f0ad7d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263647"
---
# <a name="permission-visual-basic"></a>\<izni > (Visual Basic)
Üye için gerekli izni belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `member`  
 Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru. Derleyici belirli kod öğesi var. çevirir olup olmadığını denetler ve `member` kurallı öğesi adı ' % s'çıkış XML dosyası. İçine `member` tırnak işaretleri ("").  
  
 `description`  
 Üye erişimi açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<permission>` üyenin erişim belgelemek için etiket. Kullanım <xref:System.Security.PermissionSet> sınıfın üyesi erişimi belirtin.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<permission>` açıklayan için etiket <xref:System.Security.Permissions.FileIOPermission> gerektirdiği `ReadFile` yöntemi.  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
