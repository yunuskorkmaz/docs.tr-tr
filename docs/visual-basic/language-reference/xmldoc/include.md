---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: df8749ca9d6c92cf9ef95f03eea2704812ff495a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872879"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)

Kaynak kodunuzda türleri ve üyeleri açıklayan başka bir dosya anlamına gelir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametreler  

 `filename`  
 Gereklidir. Belgeleri içeren dosyanın adı. Dosya adı bir yol ile nitelenebilir. `filename`Çift tırnak işaretleri ("") içine alın.  
  
 `tagpath`  
 Gereklidir. İçindeki etiketlerin yolu, etikete yol `filename` açar `name` . Yolu çift tırnak işaretleri ("") içine alın.  
  
 `name`  
 Gereklidir. Yorumlarla önce gelen etiketteki ad belirleyicisi. `Name` , olur `id` .  
  
 `id`  
 Gereklidir. Açıklamaların önündeki etiketin KIMLIĞI. KIMLIĞI tek tırnak işareti (' ') içine alın.  
  
## <a name="remarks"></a>Açıklamalar  

 `<include>`Kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmak için etiketini kullanın. Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.  
  
 `<include>`Etıketı W3C XML Path Language (XPath) sürüm 1,0 önerisini kullanır. Kullanımı özelleştirmenin yolları hakkında daha fazla bilgi için `<include>` bkz <https://www.w3.org/TR/xpath> ..  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<include>` adlı bir dosyadan üye belge açıklamalarını içeri aktarmak için etiketini kullanır `commentFile.xml` .  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
