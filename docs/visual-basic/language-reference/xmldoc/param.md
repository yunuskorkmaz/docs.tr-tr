---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 476b3f4f6b85908897e15f73bc23d2b060e337c3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283653"
---
# <a name="param-visual-basic"></a>\<param > (Visual Basic)
Bir parametre adı ve açıklama tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Bir yöntem parametresi adı. Adı çift tırnak içine alın ("").  
  
 `description`  
 Parametre için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 `<param>` Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.  
  
 Metni `<param>` etiketi aşağıdaki konumlarda gösterilir:  
  
-   IntelliSense, parametre bilgisi. Daha fazla bilgi için [IntelliSense kullanarak](/visualstudio/ide/using-intellisense).  
  
-   Nesne Tarayıcısı. Daha fazla bilgi için [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<param>` açıklamak için etiket `id` parametresi.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
