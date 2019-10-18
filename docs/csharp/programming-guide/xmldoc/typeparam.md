---
title: <typeparam> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: e5e0d7be46e02bd30799b54246db729ae63ca300
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523291"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parametreler  
 `name`  
 Tür parametresinin adı. Adı çift tırnak işareti ("") içine alın.  
  
 `description`  
 Tür parametresi için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 etiketi, bir tür parametresini betimleyen genel tür veya yöntem bildirimine ilişkin açıklamada kullanılmalıdır. Genel tür veya metodun her tür parametresi için bir etiket ekleyin.  
  
 Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).  
  
 @No__t_0 etiketinin metni IntelliSense 'de, [nesne tarayıcısı pencere](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu açıklama Web raporunda görüntülenir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
