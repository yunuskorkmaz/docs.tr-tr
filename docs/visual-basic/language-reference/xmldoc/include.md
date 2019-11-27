---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348458"
---
# <a name="include-visual-basic"></a>\<içerme > (Visual Basic)
Kaynak kodunuzda türleri ve üyeleri açıklayan başka bir dosya anlamına gelir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametreler  
 `filename`  
 Gerekli. Belgeleri içeren dosyanın adı. Dosya adı bir yol ile nitelenebilir. `filename` çift tırnak işaretleri ("") içine alın.  
  
 `tagpath`  
 Gerekli. `filename` etiket `name`yol gösteren etiketlerin yolu. Yolu çift tırnak işaretleri ("") içine alın.  
  
 `name`  
 Gerekli. Yorumlarla önce gelen etiketteki ad belirleyicisi. `Name` bir `id`olacaktır.  
  
 `id`  
 Gerekli. Açıklamaların önündeki etiketin KIMLIĞI. KIMLIĞI tek tırnak işareti (' ') içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmak için `<include>` etiketini kullanın. Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.  
  
 `<include>` etiketinde W3C XML Path Language (XPath) sürüm 1,0 önerisi kullanılır. `<include>` kullanımını özelleştirmenin yolları hakkında daha fazla bilgi için bkz. <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `commentFile.xml`adlı bir dosyadan üye belge açıklamalarını içeri aktarmak için `<include>` etiketini kullanır.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 `commentFile.xml` biçimi aşağıdaki gibidir.  
  
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
