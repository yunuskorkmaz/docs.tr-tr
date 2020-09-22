---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0846efbaf2afacd3d0783a2d2d8e4dae3fc8b715
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872707"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)

İçeriğin bir paragraf olarak biçimlendirildiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
