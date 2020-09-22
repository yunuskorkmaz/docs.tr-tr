---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 471d3ddb5cf5a234cb77de6d1d93309faf754359
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865842"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)

Üyenin özetini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametreler  

 `description`  
 Nesnenin Özeti.  
  
## <a name="remarks"></a>Açıklamalar  

 `<summary>`Bir tür veya tür üyesini anlatmak için etiketini kullanın. [\<remarks>](remarks.md)Bir tür açıklamasına ek bilgi eklemek için kullanın.  
  
 Etiket metni, `<summary>` IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca nesne tarayıcısı görüntülenir. Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<summary>` `ResetCounter` yöntemini ve özelliğini anlatmak için etiketini kullanır `Counter` .  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
