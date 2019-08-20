---
title: <seealso> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
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
ms.openlocfilehash: 3ddaa7efec2b4bf5ffa53971aa6f380a1be9bad8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587663"
---
# <a name="seealso-c-programming-guide"></a>\<SeeAlso > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında `member` öğe adına geçirir.`member` Çift tırnak işaretleri ("") içinde yer almalıdır.  
  
 Genel bir türe [ \<](./see.md)cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. >.  
  
## <a name="remarks"></a>Açıklamalar  
 \<SeeAlso > etiketi de Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır. Metnin içinden bir bağlantı belirtmek için [ \<> göster](./see.md) ' i kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bkz. SeeAlso > kullanımı \<örneği için bkz [ \<. Summary >](./summary.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
