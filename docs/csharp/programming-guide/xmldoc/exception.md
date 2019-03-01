---
title: <exception> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: b316927c5dfd5eda05bea653f9a601cca9865af3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982069"
---
# <a name="exception-c-programming-guide"></a>\<Özel Durum > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru. Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası. `member` çift tırnak içinde yer almalıdır ("").  
  
 Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz. [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Özel durumun açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Özel durum > etiketi hangi özel durumlar atılabilir belirtmenize olanak sağlar. Bu etiket, yöntemleri, özellikleri, olayları ve dizin oluşturucular için tanımlarına uygulanabilir.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
 Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../../../csharp/programming-guide/exceptions/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
