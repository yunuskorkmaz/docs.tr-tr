---
title: <value> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 09577d931c6b1f571cd4112c788da38bab85bf42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523271"
---
# <a name="value-c-programming-guide"></a>\<value > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametreler  
 `property-description`  
 Özelliği için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0value > etiketi, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar. Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için bir [\<summary >](./summary.md) etiketi ekleneceğini unutmayın. Sonra özelliğin temsil ettiği değeri tanımlayan bir \<value > etiketini el ile eklemeniz gerekir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
