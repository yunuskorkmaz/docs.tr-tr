---
title: <exception> C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 4e4204996c006ce6e943c9a09661001b0e0c2a14
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523464"
---
# <a name="exception-c-programming-guide"></a>\<exception > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametreler  
 cref = "`member`"  
 Geçerli derleme ortamında kullanılabilir bir özel duruma başvuru. Derleyici verilen özel durumun var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir. `member` çift tırnak işaretleri ("") içinde yer almalıdır.  
  
 Genel bir türe başvurmak üzere `member` biçimlendirme hakkında daha fazla bilgi için bkz. [XML dosyasını işleme](processing-the-xml-file.md).
  
 `description`  
 Özel durumun açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0exception > etiketi hangi özel durumların atılamayacağını belirlemenizi sağlar. Bu etiket Yöntemler, özellikler, olaylar ve Dizin oluşturucular için tanımlara uygulanabilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
 Özel durum işleme hakkında daha fazla bilgi için bkz. [özel durumlar ve özel durum işleme](../exceptions/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](recommended-tags-for-documentation-comments.md)
