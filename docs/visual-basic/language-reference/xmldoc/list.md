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
ms.openlocfilehash: 7d7b85867f4c701322c5e6c31f2d89ab38fad05d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818542"
---
# <a name="list-visual-basic"></a>\<Liste > (Visual Basic)
Bir listeyi veya tabloyu tanımlar.  
  
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
 Liste türü. "Bullet" bir madde işaretli liste, numaralandırılmış liste veya iki sütunlu bir tablo için "Tablo" için "number" olmalıdır.  
  
 `term`  
 Yalnızca ne zaman kullanılır `type` "Tablo" olan Açıklama etiketi tanımlanan tanımlamak için bir terim.  
  
 `description`  
 Zaman `type` "bullet" veya "number" `description` listesinde bir öğe olduğunda `type` "Tablo" olan `description` tanımı `term`.  
  
## <a name="remarks"></a>Açıklamalar  
 `<listheader>` Blok başlığı bir tablo veya tanım listesi tanımlar. Bir tablo tanımlarken, yalnızca bir giriş sağlamanız gerekir `term` başlığı.  
  
 Listedeki her bir öğe ile belirtilen bir `<item>` blok. Tanım listesi oluştururken, her ikisini de belirtmelisiniz `term` ve `description`. Ancak, bir tablo, madde işaretli liste veya numaralı liste için yalnızca bir giriş sağlamanız gerekir `description`.  
  
 Bir listeyi veya tabloyu kadar olabilir `<item>` gerektiğinde engeller.  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<list>` etiket açıklamalar bölümünde bir madde işaretli liste tanımlamak için.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
