---
title: <inheritdoc> C# Programlama Kılavuzu
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795163"
---
# <a name="inheritdoc-c-programming-guide"></a>\<ınherbir doc >C# (Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a>Devralma belgesi

Temel sınıflardan, arabirimlerden ve benzer metotlardan XML açıklamalarını devralma. Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar. 
  
## <a name="remarks"></a>Açıklamalar  
XML yorumlarınızı temel sınıflara veya arabirimlere ekleyin ve ınherıng doc 'in, sınıfları uygulama açıklamalarını kopyalamasına izin verin.

XML yorumlarınızı zaman uyumlu yöntemlerinize ekleyin ve ınherelidoc 'in açıklamaları aynı yöntemlerin zaman uyumsuz sürümlerine kopyalamasını sağlayın.  

Belirli bir üyeden açıklamaları kopyalamak istiyorsanız, üyeyi belirtmek için `cref` özniteliğini kullanabilirsiniz.
  
## <a name="examples"></a>Örnekler
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
