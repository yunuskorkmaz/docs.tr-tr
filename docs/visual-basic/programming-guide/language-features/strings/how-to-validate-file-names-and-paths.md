---
title: "Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama
Bu örnek döndüren bir `Boolean` bir dize bir dosya adı veya yolu temsil edip etmediğini gösteren değer. Doğrulama adı dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Bu örnek adı yanlış iki nokta üst üste veya dizinleri adı olmayan yerleştirdiğini veya adının uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor denetlemez. Bu da uygulama belirtilen ada sahip dosya sistemi kaynağa erişmek için izni olup olmadığını kontrol etmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
