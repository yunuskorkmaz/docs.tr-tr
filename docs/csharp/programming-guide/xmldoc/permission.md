---
title: "&lt;izin&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37bb37ea14edc1f91225f9b04b18b354d99579b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpermissiongt-c-programming-guide"></a>&lt;izin&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru. Verilen code öğesi var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı. *üye* çift tırnak işaretleri içinde görünmesi gerekir ("").  
  
 Genel bir tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Üye erişimi açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 \<İzni > etiketi üyesi erişim belge olanak sağlar. <xref:System.Security.PermissionSet> Sınıfı üyesi erişmesine olanak sağlar.  
  
 İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
