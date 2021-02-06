---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <seealso> (Visual Basic)'
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0bf6fa69ad63db016b42e31f717f521f82bbe20e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640322"
---
# <a name="seealso-visual-basic"></a>\<seealso> (Visual Basic)

Ayrıca bkz. bölümünde görüntülenen bir bağlantı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  

 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir. `member` Çift tırnak işaretleri ("") içinde yer almalıdır.  
  
## <a name="remarks"></a>Açıklamalar  

 `<seealso>`Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtmek için etiketini kullanın. [\<see>](see.md)Metnin içinden bir bağlantı belirtmek için kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<seealso>` `DoesRecordExist` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `UpdateRecord` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
