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
ms.openlocfilehash: 430270c170f2829d9bf9b90d258c948176b9c086
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523332"
---
# <a name="seealso-c-programming-guide"></a>\<seealso > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 cref = "`member`"  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir. `member` Çift tırnak işaretleri ("") içinde yer almalıdır.  
  
 Genel bir türe cref başvurusu oluşturma hakkında bilgi için bkz. [\<see >](./see.md).  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0seealso > etiketi, Ayrıca bkz. bölümünde görünmesini isteyebileceğiniz metni belirtmenize olanak tanır. Metnin içinden bir bağlantı belirtmek için [\<see >](./see.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 @No__t_2seealso > kullanma örneği için bkz. [\<summary >](./summary.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
