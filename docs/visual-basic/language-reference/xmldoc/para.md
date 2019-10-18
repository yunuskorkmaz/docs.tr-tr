---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524731"
---
# <a name="para-visual-basic"></a>\<para > (Visual Basic)
İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametreler  
 `content`  
 Paragrafın metni.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 etiketi, [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)veya [\<returns](../../../visual-basic/language-reference/xmldoc/returns.md)> gibi bir etiket içinde kullanım içindir ve metne yapı eklemenizi sağlar.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `UpdateRecord` yönteminin açıklamalar bölümünü iki paragrafa bölmek için `<para>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
