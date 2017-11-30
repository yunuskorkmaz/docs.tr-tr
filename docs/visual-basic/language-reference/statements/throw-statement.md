---
title: Throw Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Throw
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ada551c32b8296f0dad2ae929ca9c81a14a711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **Modülü:**`Interaction`  
  
 **Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Try... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
