---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 90f358aad8e3219b2e3cb3e9b996a24b3138828b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970837"
---
# <a name="remarks-visual-basic"></a>\<REMARKS > (Visual Basic)
Üye için Açıklamalar bölümüne belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `description`  
 Üye açıklaması.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `<remarks>` ile belirtilen bilgileri ekleme, bir tür hakkında bilgi eklemek için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md).  
  
 Bu bilgiler, Nesne Tarayıcısı'nda görüntülenir. Nesne tarayıcı hakkında daha fazla bilgi için bkz: [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `<remarks>` ne açıklamak için etiket `UpdateRecord` yöntemi yapar.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
