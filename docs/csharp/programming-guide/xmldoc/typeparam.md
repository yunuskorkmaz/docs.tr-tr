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
ms.openlocfilehash: 9150ab3e29eaa6b692e2ab2be90bb0e87ba54941
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978668"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `name`  
 Tür parametresinin adı. Adı çift tırnak içine alın ("").  
  
 `description`  
 Tür parametresi için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 `<typeparam>` Etiketi genel bir tür veya yöntem bildirimi için açıklama açıklayan bir tür parametresi için kullanılmalıdır. Genel tür veya yöntemin her tür parametresi için bir etiket ekleyin.  
  
 Daha fazla bilgi için [genel türler](../../../csharp/programming-guide/generics/index.md).  
  
 Metni `<typeparam>` etiketi IntelliSense içinde gösterilecek [nesne tarayıcı penceresi](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kod açıklaması web rapor.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
