---
title: Throw Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: c17adc6df0f8cf94f06547b48a32b2ffb8f303ca
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973489"
---
# <a name="throw-statement-visual-basic"></a>Throw Deyimi (Visual Basic)
Bir yordam içinde özel durum oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Bölümü  
 `expression`  
 Özel durum oluşturulmasına hakkında bilgi sağlar. Bulunan, isteğe bağlı bir `Catch` deyimi, aksi takdirde gereklidir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Throw` Deyimi, yapılandırılmış özel durum işleme kodu ile işleyebilmeniz bir özel durum oluşturur (`Try`... `Catch`... `Finally`) ya da yapılandırılmamış özel durum işleme kodunu (`On Error GoTo`). Kullanabileceğiniz `Throw` uygun özel durum işleme kodu bulana kadar Visual Basic çağrı yığınında yukarı taşır. çünkü, kod içindeki hataları yakalamak için deyimi.  
  
 A `Throw` herhangi bir ifade deyimi yalnızca kullanılabilir bir `Catch` deyimi, case deyiminde tarafından işlenmekte olan özel durum beklerseniz `Catch` deyimi.  
  
 `Throw` Deyimi için çağrı yığınını sıfırlar `expression` özel durum. Varsa `expression` sağlanmadı, çağrı yığını sol değiştirilmez. Bir özel durum için çağrı yığınını erişebileceğiniz <xref:System.Exception.StackTrace%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `Throw` deyimi bir özel durum:  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modül:** `Interaction`  
  
 **Derleme:** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
