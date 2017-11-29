---
title: '&lt;dahil&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22eebaa8da8ef082e132cfdf8cb68498bfe16d73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltincludegt-visual-basic"></a>&lt;dahil&gt; (Visual Basic)
Türleri ve kaynak kodunuzu üyeleri tanımlayan başka bir dosyaya başvuruyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametreler  
 `filename`  
 Gerekli. Belgeleri içeren dosyanın adı. Dosya adı nitelenmiş bir yol olmalıdır. İçine `filename` çift tırnak işaretleri ("").  
  
 `tagpath`  
 Gerekli. Etiketleri yolunu `filename` etikete müşteri adayları `name`. Yolu çift tırnak işaretleri içine alın ("").  
  
 `name`  
 Gerekli. Açıklamaları önündeki etiketinde ad tanımlayıcısı. `Name`sahip bir `id`.  
  
 `id`  
 Gerekli. Açıklamaları önündeki etiket kimliği. Kimliği tek tırnak işaretleri içine alın (' ').  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<include>` etiketi başka bir dosya türlerini tanımlamak açıklamaları ve kaynak kodunuzu üyelerinde bakın. Bu belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek alternatiftir.  
  
 `<include>` Etiketini W3C XML Path dili (XPath) sürüm 1.0 öneri kullanır. Daha fazla bilgi için özelleştirme yolları, `<include>` http://www.w3.org/TR/xpath kullanım kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<include>` üye belge açıklamaları olarak adlandırılan bir dosyadan içeri aktarmak için etiket `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Biçimi `commentFile.xml` aşağıdaki gibidir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
