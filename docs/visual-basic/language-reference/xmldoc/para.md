---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400079"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)
İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametreler  
 `content`  
 Paragrafın metni.  
  
## <a name="remarks"></a>Açıklamalar  
 `<para>`Etiketi,, veya gibi bir etiket içinde kullanım içindir [\<summary>](summary.md) [\<remarks>](remarks.md) [\<returns>](returns.md) ve metne yapı eklemenizi sağlar.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `<para>` yöntemi için açıklamalar bölümünü iki paragrafa bölmek için etiketini kullanır `UpdateRecord` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
