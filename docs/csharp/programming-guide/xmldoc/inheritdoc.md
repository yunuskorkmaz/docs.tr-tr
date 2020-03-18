---
title: <inheritdoc>- C# Programlama Kılavuzu
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156954"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>Kalıtsal Doküman

Temel sınıflardan, arabirimlerden ve benzer yöntemlerden XML yorumlarını devredin. Bu, yinelenen XML yorumlarının istenmeyen kopyalanması ve yapıştırMasını ortadan kaldırır ve XML yorumlarını otomatik olarak senkronize eder.
  
## <a name="remarks"></a>Açıklamalar  
XML yorumlarınızı temel sınıflara veya arabirimlere ekleyin ve InheritDoc'un açıklamaları uygulama sınıflarına kopyalamasına izin verin.

XML yorumlarınızı eşzamanlı yöntemlerinize ekleyin ve InheritDoc'un yorumları aynı yöntemlerin eşzamanlı sürümlerine kopyalamasına izin verin.  

Belirli bir üyenin yorumlarını kopyalamak istiyorsanız, `cref` üyeyi belirtmek için özniteliği kullanabilirsiniz.
  
## <a name="examples"></a>Örnekler
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dokümantasyon Yorumları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
