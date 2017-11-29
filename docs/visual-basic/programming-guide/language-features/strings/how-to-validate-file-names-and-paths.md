---
title: "Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c50d09dd7160992ffd95ececeff623a8aa93d2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama
Bu örnek döndüren bir `Boolean` bir dize bir dosya adı veya yolu temsil edip etmediğini gösteren değer. Doğrulama adı dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Bu örnek adı yanlış iki nokta üst üste veya dizinleri adı olmayan yerleştirdiğini veya adının uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor denetlemez. Bu da uygulama belirtilen ada sahip dosya sistemi kaynağa erişmek için izni olup olmadığını kontrol etmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
