---
title: "&lt;SeeAlso&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 088445680375e1c1805f9fb4356fe98c730178e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;SeeAlso&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru. Verilen code öğesi var ve geçirir derleyici denetler `member` çıktı XML öğesi adı.`member` çift tırnak işaretleri içinde görünmesi gerekir ("").  
  
 Genel bir tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md).  
  
## <a name="remarks"></a>Açıklamalar  
 \<Seealso > etiketi bir Ayrıca bkz. bölümünde görünen isteyebilirsiniz metin belirtmenize olanak sağlar. Kullanım [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md) metin içindeki bir bağlantıdan belirtmek için.  
  
 İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 Bkz: [ \<Özet >](../../../csharp/programming-guide/xmldoc/summary.md) kullanma örneği için \<seealso >.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
