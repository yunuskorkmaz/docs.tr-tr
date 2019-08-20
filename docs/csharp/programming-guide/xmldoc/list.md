---
title: <list> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: aadb24c43d49acb3e71490efd156b14d9fc5f133
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587978"
---
# <a name="list-c-programming-guide"></a>\<Liste > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
## <a name="parameters"></a>Parametreler  
 `term`  
 ' De `description`tanımlanacak bir terim.  
  
 `description`  
 Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir `term`tanımı.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Listheader > bloğu, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır. Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.  
  
 Listedeki her öğe bir \<öğe > bloğuyla belirtilir. Bir tanım listesi oluştururken, hem hem `term` `description`de belirtmeniz gerekecektir. Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş `description`sağlamanız gerekir.  
  
 Bir liste veya tablo, gereken sayıda \<öğe > bloğuyla bulunabilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
