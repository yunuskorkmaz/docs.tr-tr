---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352199"
---
# <a name="summary-visual-basic"></a>\<Özet > (Visual Basic)
Üyenin özetini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametreler  
 `description`  
 Nesnenin Özeti.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir tür veya tür üyesini anlatmak için `<summary>` etiketini kullanın. Bir tür açıklamasına ek bilgi eklemek için [\<açıklamaları >](../../../visual-basic/language-reference/xmldoc/remarks.md) kullanın.  
  
 `<summary>` etiketinin metni, IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca Nesne Tarayıcısı görüntülenir. Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `ResetCounter` yöntemini ve `Counter` özelliğini anlatmak için `<summary>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
