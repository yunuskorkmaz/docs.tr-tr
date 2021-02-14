---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic Nothing ve dizeler'
title: Nothing ve Dizeler
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: a32dd8b38033f1845f2ada87bf5f538d45fede18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424352"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic'de Dizeler ve Nothing

Visual Basic çalışma zamanı ve .NET Framework, `Nothing` dizelere geldiğinde farklı şekilde değerlendirilir.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Çalışma zamanı ve .NET Framework Visual Basic  

 Aşağıdaki örneği inceleyin:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic çalışma zamanı genellikle `Nothing` boş bir dize ("") olarak değerlendirilir. .NET Framework, ancak üzerinde bir dize işlemi gerçekleştirmek için bir girişimde bulunulduğunda bir özel durum oluşturur `Nothing` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
