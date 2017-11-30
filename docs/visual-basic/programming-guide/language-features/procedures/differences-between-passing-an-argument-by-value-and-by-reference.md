---
title: "Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3efd4f41184287cdcd3d499712a857bee997c1a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar (Visual Basic)
Bir yordama bağımsız değişkenlerden biri veya daha fazla geçirdiğinizde, her bir bağımsız değişkeni çağıran kodu temel programlama öğesi karşılık gelir. Bu temel alınan öğenin değerini ya da bir başvuru geçirebilirsiniz. Bu olarak bilinir *mekanizması geçirme*.  
  
## <a name="passing-by-value"></a>Değere göre geçirme  
 Bağımsız değişken geçirmek *değeriyle* belirterek [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamı tanımında karşılık gelen bir parametre için anahtar sözcük. Bu mekanizma, geçirme kullandığınızda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yordamı yerel bir değişkende içine temel programlama öğesinin değeri kopyalar. Yordamı kod, çağıran kodu temel öğesine herhangi bir erişim yok.  
  
## <a name="passing-by-reference"></a>Başvuruya göre geçirme  
 Bağımsız değişken geçirmek *başvuruya* belirterek [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) yordamı tanımında karşılık gelen bir parametre için anahtar sözcük. Bu mekanizma, geçirme kullandığınızda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yordamı çağıran kodu temel programlama öğesi için doğrudan bir başvuru sağlar.  
  
## <a name="passing-mechanism-and-element-type"></a>Geçirme mekanizması ve öğe türü  
 Mekanizması geçirme seçeneğiniz sınıflandırması, temel alınan öğe türü ile aynı değil. Değere veya başvuruya göre geçirme ne başvurur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yordamı kodu sağlar. Bir değer veya başvuru türü bir programlama öğesi bellekte nasıl depolandığını için ifade eder.  
  
 Ancak, öğe türü ve geçirme mekanizması birbirleriyle ilişkilidir. Bir başvuru türü değeri bellek verilerde başka bir yerde bir işaretçidir. Temel alınan öğe erişemiyor olsa bile bu değere göre bir başvuru türü geçirdiğinizde, yordam kodu temel alınan öğenin veri için bir işaretçi olduğu anlamına gelir. Örneğin, bir dizi değişkeni öğesiyse yordamı kod değişken erişimi yok, ancak dizi üyeleri erişebilir.  
  
## <a name="ability-to-modify"></a>Değiştirme olanağı  
 Bağımsız değişken olarak bir değiştirilemez öğesi geçirdiğinizde, kendisine geçirilen olup olmadığını yordamı hiçbir zaman arama kodda değiştirebilirsiniz `ByVal` veya `ByRef`.  
  
 Değiştirilebilir bir öğesi için öğe türü ve geçirme mekanizması arasındaki etkileşim aşağıdaki tabloda özetlenmiştir.  
  
|Öğe türü|Geçirilen`ByVal`|Geçirilen`ByRef`|  
|------------------|--------------------|--------------------|  
|Değer türü (yalnızca bir değer içerir)|Yordamı, değişken veya üyeleri hiçbirini değiştiremezsiniz.|Yordam, değişken ve üyelerini değiştirebilirsiniz.|  
|Başvuru türü (bir sınıf veya yapı örneği için bir işaretçi içerir)|Yordam değişkeni değiştiremez ancak işaret ettiği örnek üyeleri değiştirebilir.|Yordam işaret ettiği örnek üyelerinin ve değişkenini değiştirebilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız değişkenleri konuma göre ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
