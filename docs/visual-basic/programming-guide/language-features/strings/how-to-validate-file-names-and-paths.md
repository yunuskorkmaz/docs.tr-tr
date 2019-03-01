---
title: "Nasıl yapılır: Dosya adlarını ve yollarını Visual Basic'te doğrulama"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975530"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Nasıl yapılır: Dosya adlarını ve yollarını Visual Basic'te doğrulama
Bu örnekte döndürür bir `Boolean` bir dizenin bir dosya adı veya yolu temsil edip etmediğini belirten değer. Doğrulama adı dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Bu örnekte, iki nokta üst üste veya dizin adı olmayan adı yanlış yerleştirdiğini veya adı sistem tarafından tanımlanan uzunluk üst sınırını aşıyor denetlemez. Bu da uygulamanın belirtilen ada sahip dosya sistemi kaynak erişim izni olup olmadığını denetlemez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
