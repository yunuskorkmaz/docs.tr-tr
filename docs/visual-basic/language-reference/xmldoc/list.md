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
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400092"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
Bir liste veya tablo tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Yalnızca "Table" olduğunda kullanılır `type` . Description etiketinde tanımlanan, tanımlanacak bir terim.  
  
 `description`  
 " `type` İtem" veya "Number" olduğunda, " `description` Tablo", `type` `description` tanımdır `term` .  
  
## <a name="remarks"></a>Açıklamalar  
 `<listheader>`Blok, bir tablo ya da tanım listesinin başlığını tanımlar. Tablo tanımlarken, yalnızca başlıkta bir giriş sağlamanız gerekir `term` .  
  
 Listedeki her öğe bir `<item>` blokla belirtilir. Bir tanım listesi oluştururken, hem hem de belirtmeniz gerekir `term` `description` . Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş sağlamanız gerekir `description` .  
  
 Bir liste veya tablo gerektiği kadar çok `<item>` blok içerebilir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `<list>` açıklamalar bölümünde madde işaretli bir liste tanımlamak için etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
