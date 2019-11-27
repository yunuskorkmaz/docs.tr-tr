---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354317"
---
# <a name="code-visual-basic"></a>\<kodu > (Visual Basic)
Metnin birden çok kod satırı olduğunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Parametreler  
 `content`  
 Kod olarak işaretlemek için metin.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden çok satırı kod olarak göstermek için `<code>` etiketini kullanın. Bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için [\<c >](../../../visual-basic/language-reference/xmldoc/c.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `ID` alanının kullanılmasına ilişkin örnek kodu eklemek için \<Code > etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
