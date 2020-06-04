---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 24358a1b004f1cefbfeb3fb8451380ed883841df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411479"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)
Bir özelliğin açıklamasını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametreler  
 `property-description`  
 Özelliği için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 `<value>`Bir özelliği anlatmak için etiketini kullanın. Visual Studio geliştirme ortamındaki kod Sihirbazı 'nı kullanarak bir özellik eklediğinizde, [\<summary>](summary.md) yeni özellik için bir etiket ekleneceğini unutmayın. Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `<value>` özelliğin hangi değere sahip olduğunu belirlemek için etiketini kullanır `Counter` .  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
