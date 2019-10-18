---
title: <remarks> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 508201fed57fce93b64691de55dce45780adc13c
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523349"
---
# <a name="remarks-c-programming-guide"></a>\<remarks > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parametreler  
 `Description`  
 Üyenin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0remarks > etiketi, [\<summary >](./summary.md)ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır. Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
