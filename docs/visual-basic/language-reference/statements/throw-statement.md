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
ms.openlocfilehash: 9680700267f17c8e316de351fead61f1dc4aded0
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869018"
---
# <a name="throw-statement-visual-basic"></a>Throw Deyimi (Visual Basic)

Bir yordam içinde özel durum oluşturur.

## <a name="syntax"></a>Sözdizimi

```vb
Throw [ expression ]
```

## <a name="part"></a>Bölümüyle

`expression`\
Oluşturulacak özel durum hakkında bilgi sağlar. Bir `Catch` bildirimde bulunduğunda isteğe bağlı, aksi takdirde gereklidir.

## <a name="remarks"></a>Açıklamalar

Bu `Throw` ifade, yapılandırılmış özel durum işleme kodu (`Try`...) ile işleyebileceğiniz bir özel durum oluşturur. `Catch`... ) veya yapılandırılmamış özel durum işleme kodu (`On Error GoTo`). `Finally` Bu ifadeyi, `Throw` uygun özel durum işleme kodunu bulana kadar çağrı yığınını Visual Basic, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.

İfadesi `Throw` olmayan bir deyim yalnızca bir `Catch` deyimde kullanılabilir, bu durumda deyim deyim tarafından `Catch` işlenmekte olan özel durumu yeniden oluşturur.

İfade, `expression` özel durum için çağrı yığınını sıfırlar. `Throw` `expression` Sağlanmazsa, çağrı yığını değişmeden bırakılır. Özel durum için çağrı yığınına <xref:System.Exception.StackTrace%2A> özelliği aracılığıyla erişebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod bir özel durum `Throw` oluşturmak için ifadesini kullanır:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
