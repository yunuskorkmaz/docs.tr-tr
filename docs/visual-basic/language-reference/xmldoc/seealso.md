---
title: '&lt;SeeAlso&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a1acbf2ee8f416e28987cc9d63dd3bf6d8c2dcf3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltseealsogt-visual-basic"></a>&lt;SeeAlso&gt; (Visual Basic)
Ayrıca bkz. bölümünde görünen bağlantı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `member`  
 Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru. Verilen code öğesi var ve geçirir derleyici denetler `member` çıktı XML öğesi adı. `member`çift tırnak işaretleri içinde görünmesi gerekir ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<seealso>` etiketi bir Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtin. Kullanım [ \<bkz >](../../../visual-basic/language-reference/xmldoc/see.md) metin içindeki bir bağlantıdan belirtmek için.  
  
 İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<seealso>` içinde etiketi `DoesRecordExist` başvurmak için bölüm açıklamalar `UpdateRecord` yöntemi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
