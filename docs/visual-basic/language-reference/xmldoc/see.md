---
description: 'Hakkında daha fazla bilgi edinin: <see> (Visual Basic)'
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 46dd67710f83d6c4549ddfeb6b7bbc1503b7aa1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640348"
---
# <a name="see-visual-basic"></a>\<see> (Visual Basic)

Başka bir üyeye bağlantı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  

 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir. `member` Çift tırnak işaretleri ("") içinde yer almalıdır.  
  
## <a name="remarks"></a>Açıklamalar  

 `<see>`Metnin içinden bir bağlantı belirtmek için etiketini kullanın. [\<seealso>](seealso.md)"Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<see>` `UpdateRecord` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `DoesRecordExist` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
