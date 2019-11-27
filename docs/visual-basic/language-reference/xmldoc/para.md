---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 8f28ecc33eea99150509bb4bade047489b4b826b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352311"
---
# <a name="para-visual-basic"></a>\<paragraf > (Visual Basic)
İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametreler  
 `content`  
 Paragrafın metni.  
  
## <a name="remarks"></a>Açıklamalar  
 `<para>` etiketi, bir etiket içinde kullanılmak üzere, [\<özet >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<açıklamaları >](../../../visual-basic/language-reference/xmldoc/remarks.md)veya [\<> döndürür](../../../visual-basic/language-reference/xmldoc/returns.md)ve metne yapı eklemenizi sağlar.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `UpdateRecord` yönteminin açıklamalar bölümünü iki paragrafa bölmek için `<para>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
