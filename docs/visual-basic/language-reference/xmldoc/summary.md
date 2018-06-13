---
title: '&lt;Özet&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: cf320b61a2ca1c54b22e3c3d31ae51d003366efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602658"
---
# <a name="ltsummarygt-visual-basic"></a>&lt;Özet&gt; (Visual Basic)
Üye özetini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `description`  
 Nesne özeti.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<summary>` bir tür veya bir tür üyesi açıklamak için etiket. Kullanım [ \<açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md) türü açıklaması için ek bilgiler eklemek için.  
  
 Metni `<summary>` etiket IntelliSense türüyle ilgili bilgiler yalnızca kaynağı ve ayrıca nesne tarayıcısında görüntülenir. Nesne Tarayıcısı hakkında daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<summary>` açıklamak için etiket `ResetCounter` yöntemi ve `Counter` özelliği.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
