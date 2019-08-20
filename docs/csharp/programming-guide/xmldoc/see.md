---
title: <see>- C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: e292e116ac468246bfe81e1eb5d5c5819a506701
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587692"
---
# <a name="see-c-programming-guide"></a>\<bkz. >C# (Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parametreler  
 cref = " `member`"  
 Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru. Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında `member` öğe adına geçirir. *Üyeyi* çift tırnak işareti ("") içine koyun.  
  
## <a name="remarks"></a>Açıklamalar  
 > \<Etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır. Ayrıca, metnin See de bir bölümüne yerleştirilmesi gerektiğini belirtmek için [ \<de seede >](./seealso.md) kullanın. Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.  
  
 Aşağıdaki örnek bir Özet bölümü \<içindeki bir See > etiketini gösterir.  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge Açıklamaları için Önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
