---
title: '&lt;izni&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 1447541f7e093a7cf434702368bdce0d07c4908b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558595"
---
# <a name="ltpermissiongt-c-programming-guide"></a>&lt;izni&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru. Derleyici belirli kod öğesi var. çevirir olup olmadığını denetler ve `member` kurallı öğesi adı ' % s'çıkış XML dosyası. *üye* çift tırnak içinde yer almalıdır ("").  
  
 Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Üye erişimi açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 \<İzni > etiketi üyenin erişim belge olanak tanır. <xref:System.Security.PermissionSet> Sınıf üyesi erişimi belirtmenize olanak sağlar.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
