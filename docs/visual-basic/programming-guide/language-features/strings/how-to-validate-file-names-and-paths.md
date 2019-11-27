---
title: 'Nasıl yapılır: dosya adlarını ve yollarını doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: cc4d275d469860aa19c45ca0fe0401b709b42d82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344359"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama
Bu örnek, bir dizenin bir dosya adını veya yolunu temsil ettiğini belirten bir `Boolean` değeri döndürür. Doğrulama, adın dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Bu örnek, adın yanlış bir şekilde veya ada sahip olmayan dizinlerin mi yoksa ya da adın uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşarsa denetlemez. Ayrıca, uygulamanın, belirtilen ada sahip dosya sistemi kaynağına erişme izni olup olmadığını denetlemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Visual Basic dizeleri doğrulanıyor](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
