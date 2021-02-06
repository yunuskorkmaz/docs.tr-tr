---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <summary> (Visual Basic)'
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 4d4b1ecf0fa054eb625c1a3cf09c1cab4e661ef2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640296"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)

Üyenin özetini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametreler  

 `description`  
 Nesnenin Özeti.  
  
## <a name="remarks"></a>Açıklamalar  

 `<summary>`Bir tür veya tür üyesini anlatmak için etiketini kullanın. [\<remarks>](remarks.md)Bir tür açıklamasına ek bilgi eklemek için kullanın.  
  
 Etiket metni, `<summary>` IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca nesne tarayıcısı görüntülenir. Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `<summary>` `ResetCounter` yöntemini ve özelliğini anlatmak için etiketini kullanır `Counter` .  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Açıklama Etiketleri](index.md)
