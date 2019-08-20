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
ms.openlocfilehash: 822ca8feafe48402f8217c10ef37fcdb1576c27a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587755"
---
# <a name="remarks-c-programming-guide"></a>\<açıklamalar > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parametreler  
 `Description`  
 Üyenin açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 Açıklamalar > etiketi, [ \<Özet >](./summary.md)ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır. \< Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
