---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dosya adlarını ve yollarını doğrulama'
title: 'Nasıl Yapılır: Dosya Adlarını ve Yollarını Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 02a48ea7cbf3291cb2fe1c64c4e636a273842546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429747"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dosya Adlarını ve Yollarını Doğrulama

Bu örnek `Boolean` , bir dizenin bir dosya adı veya yolu temsil edip etmediğini gösteren bir değer döndürür. Doğrulama, adın dosya sistemi tarafından izin verilmeyen karakterler içerip içermediğini denetler.  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Bu örnek, adın yanlış bir şekilde veya ada sahip olmayan dizinlerin mi yoksa ya da adın uzunluğu sistem tarafından tanımlanan uzunluk üst sınırını aşarsa denetlemez. Ayrıca, uygulamanın, belirtilen ada sahip dosya sistemi kaynağına erişme izni olup olmadığını denetlemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Visual Basic'de Dizeleri Doğrulama](validating-strings.md)
