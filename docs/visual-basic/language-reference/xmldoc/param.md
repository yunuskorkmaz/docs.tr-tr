---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c992c96303eb1441eaf667693b7aefb5361b196c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602927"
---
# <a name="ltparamgt-visual-basic"></a>&lt;param&gt; (Visual Basic)
Bir parametre adı ve açıklama tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Yöntem parametresinin adı. Ad çift tırnak işaretleri içine alın ("").  
  
 `description`  
 Parametresi için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 `<param>` Etiketi açıklamasında bir yöntem bildirimi için parametrelerden biri yönteminde açıklamak için kullanılmalıdır.  
  
 Metni `<param>` etiket aşağıdaki konumlarda görünecektir:  
  
-   IntelliSense parametre bilgileri. Daha fazla bilgi için bkz: [kullanarak IntelliSense](/visualstudio/ide/using-intellisense).  
  
-   Nesne Tarayıcısı. Daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<param>` açıklamak için etiket `id` parametresi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
