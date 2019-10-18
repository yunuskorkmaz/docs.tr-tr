---
title: <list> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524756"
---
# <a name="list-visual-basic"></a>\<list > (Visual Basic)
Bir liste veya tablo tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>Parametreler  
 `type`  
 Listenin türü. Bir madde işaretli liste için "madde işareti", numaralandırılmış liste için "numara" veya iki sütunlu bir tablo için "Tablo" olmalıdır.  
  
 `term`  
 Yalnızca `type` "Table" olduğunda kullanılır. Description etiketinde tanımlanan, tanımlanacak bir terim.  
  
 `description`  
 @No__t_0 "Bullet" veya "Number" olduğunda `description`, `type` "Tablo" olduğunda, `description` `term` tanımıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 bloğu, bir tablo ya da tanım listesinin başlığını tanımlar. Tablo tanımlarken, yalnızca başlıktaki `term` için bir giriş sağlamanız gerekir.  
  
 Listedeki her öğe `<item>` bloğuyla belirtilir. Tanım listesi oluştururken hem `term` hem de `description` belirtmeniz gerekir. Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description` bir giriş sağlamanız gerekir.  
  
 Bir liste veya tablo gerektiği kadar çok sayıda `<item>` bloğuyla bulunabilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, açıklamalar bölümünde madde işaretli bir liste tanımlamak için `<list>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
