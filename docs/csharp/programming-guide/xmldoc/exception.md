---
title: "&lt;özel durum&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd859a09bfbe9f814bf57f0987fd49ded9ba7100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexceptiongt-c-programming-guide"></a>&lt;özel durum&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Geçerli derleme ortamından kullanılabilir bir özel durum referansı. Belirtilen özel durum var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı. `member`çift tırnak işaretleri içinde görünmesi gerekir ("").  
  
 Genel bir tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Özel durum açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Özel durum > etiketi hangi özel durum belirtmenize olanak sağlar. Bu etiket yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımları uygulanabilir.  
  
 İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.  
  
 Özel durum işleme hakkında daha fazla bilgi için bkz: [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
