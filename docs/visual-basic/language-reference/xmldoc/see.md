---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 380923c2313450afc5745b25eeea6a444705dd3f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411531"
---
# <a name="see-visual-basic"></a>\<see> (Visual Basic)
Başka bir üyeye bağlantı belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 `member`  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve `member` çıkış XML dosyasında öğe adına geçirir. `member`Çift tırnak işaretleri ("") içinde yer almalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `<see>`Metnin içinden bir bağlantı belirtmek için etiketini kullanın. [\<seealso>](seealso.md)"Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `<see>` `UpdateRecord` yöntemine başvurmak için açıklamalar bölümündeki etiketini kullanır `DoesRecordExist` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
