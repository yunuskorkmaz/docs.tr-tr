---
description: 'Hakkında daha fazla bilgi edinin: <inheritdoc> (C# Programlama Kılavuzu)'
title: <inheritdoc> -C# Programlama Kılavuzu
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 960bdfbcec1e3f6a89675273f63b6d398e44947e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719402"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Syntax  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>Devralma belgesi

Temel sınıflardan, arabirimlerden ve benzer metotlardan XML açıklamalarını devralma. Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar.
  
## <a name="remarks"></a>Açıklamalar  

XML yorumlarınızı temel sınıflara veya arabirimlere ekleyin ve ınherıng doc 'in, sınıfları uygulama açıklamalarını kopyalamasına izin verin.

XML yorumlarınızı zaman uyumlu yöntemlerinize ekleyin ve ınherelidoc 'in açıklamaları aynı yöntemlerin zaman uyumsuz sürümlerine kopyalamasını sağlayın.  

Belirli bir üyeden açıklamaları kopyalamak istiyorsanız, `cref` üyeyi belirtmek için özniteliğini kullanabilirsiniz.
  
## <a name="examples"></a>Örnekler

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
