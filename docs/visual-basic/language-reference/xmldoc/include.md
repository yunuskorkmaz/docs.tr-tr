---
title: <include> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: ea14cc8182b8917a0805fbc509a0000c6df67462
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267046"
---
# <a name="include-visual-basic"></a>\<Ekle > (Visual Basic)
Türler ve üyeler, kaynak kodunuzdaki açıklayan başka bir dosyaya ifade eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametreler  
 `filename`  
 Gerekli. Belgeleri içeren dosyanın adı. Dosya adını içeren bir yol nitelenmiş olmalıdır. İçine `filename` çift tırnak işaretleri ("").  
  
 `tagpath`  
 Gerekli. Etiketleri yolunu `filename` etikete müşteri adayları `name`. Yolu, çift tırnak işaretleri içine alın ("").  
  
 `name`  
 Gerekli. Yorumları önündeki etiketinde ad tanımlayıcısı. `Name` sahip bir `id`.  
  
 `id`  
 Gerekli. Yorumları önünde etiket kimliği. Kimliği tek tırnak işaretleri içine (' ').  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<include>` türlerini açıklayan yorumlar başka bir dosyaya ve kaynak kodunuzu üyelerine başvurmak için etiket. Bu belge açıklamaları doğrudan, kaynak kodu dosyasında yerleştirme için bir alternatifidir.  
  
 `<include>` Etiketini kullanır: W3C XML Path Language (XPath) sürüm 1.0 öneri. Özelleştirme yolları hakkında daha fazla bilgi için `<include>` bakın <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<include>` belge açıklamaları üye adlı bir dosyadan içeri aktarmak için etiket `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Biçimi `commentFile.xml` gibidir.  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
