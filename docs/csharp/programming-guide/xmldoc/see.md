---
title: '&lt;bkz:&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: c37ad869b3eb904377cd4470a85cd557f6560290
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737794"
---
# <a name="ltseegt-c-programming-guide"></a>&lt;bkz:&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru. Derleyici belirli kod öğesi var. başarılı olup olmadığını denetler ve `member` çıktı XML öğesi adı. Bir yerde *üye* içinde çift tırnak ("").  
  
## <a name="remarks"></a>Açıklamalar  
 \<Bakın > etiketi bağlantı metninde belirtmenize olanak sağlar. Kullanım [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) metin ayrıca bölümü yerleştirilmesi gerektiğini belirtmek için. Kullanım [cref özniteliği](../../../csharp/programming-guide/xmldoc/cref-attribute.md) iç kod öğeleri için belge sayfalarına köprüler oluşturmak için.  
  
 Derleme [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
 Aşağıdaki örnekte gösterildiği bir \<bakın > etiketi içinde Özet bölümü.  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
