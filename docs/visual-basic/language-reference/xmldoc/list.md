---
title: <list>
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
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352317"
---
# <a name="list-visual-basic"></a>\<listesi > (Visual Basic)
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
 `type` "Bullet" veya "Number" olduğunda `description`, `type` "Tablo" olduğunda, `description` `term`tanımıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `<listheader>` bloğu, bir tablo ya da tanım listesinin başlığını tanımlar. Tablo tanımlarken, yalnızca başlıktaki `term` için bir giriş sağlamanız gerekir.  
  
 Listedeki her öğe `<item>` bloğuyla belirtilir. Tanım listesi oluştururken hem `term` hem de `description`belirtmeniz gerekir. Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description`bir giriş sağlamanız gerekir.  
  
 Bir liste veya tablo gerektiği kadar çok sayıda `<item>` bloğuyla bulunabilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, açıklamalar bölümünde madde işaretli bir liste tanımlamak için `<list>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
