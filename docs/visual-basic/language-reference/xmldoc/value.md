---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <value> (Visual Basic)'
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 80a3ef875eea4418d28d60dac1818f3390c361ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640257"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)

Bir özelliğin açıklamasını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
