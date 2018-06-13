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
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602859"
---
# <a name="throw-statement-visual-basic"></a>Throw Deyimi (Visual Basic)
Bir yordam içinde bir özel durum oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Bölümü  
 `expression`  
 Özel durum hakkında bilgi sağlar. Bulunan, isteğe bağlı bir `Catch` deyimi, aksi takdirde gerekli.  
  
## <a name="remarks"></a>Açıklamalar  
 `Throw` Deyimi ile yapılandırılmış özel durum işleme kod işleyebilecek bir özel durum oluşturur (`Try`... `Catch`... `Finally`) veya yapılandırılmamış özel durum işleme kod (`On Error GoTo`). Kullanabileceğiniz `Throw` uygun özel durum işleme kodu bulana kadar Visual Basic çağrı yığınına taşıdığı için kodunuzu içindeki hataları yakalamak için deyimi.  
  
 A `Throw` hiçbir ifade deyimiyle yalnızca kullanılabilir bir `Catch` durumda deyim şu anda tarafından işlenen özel durum bloğunu deyimi `Catch` deyimi.  
  
 `Throw` Deyimi için çağrı yığını sıfırlar `expression` özel durum. Varsa `expression` sağlanmaz, çağrı yığını sol haliyle aynıdır. Çağrı yığını ile özel durum için erişim <xref:System.Exception.StackTrace%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `Throw` deyimi bir özel durum:  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Modülü:** `Interaction`  
  
 **Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
