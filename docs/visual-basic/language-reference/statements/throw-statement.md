---
title: Throw Deyimi
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
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352792"
---
# <a name="throw-statement-visual-basic"></a>Throw Deyimi (Visual Basic)

Bir yordam içinde özel durum oluşturur.

## <a name="syntax"></a>Sözdizimi

```vb
Throw [ expression ]
```

## <a name="part"></a>Bölümüyle

`expression`\
Oluşturulacak özel durum hakkında bilgi sağlar. `Catch` bildiriminde bulunduğunda isteğe bağlı, aksi takdirde gereklidir.

## <a name="remarks"></a>Açıklamalar

`Throw` ifade, yapılandırılmış özel durum işleme kodu (`Try`...`Catch`...`Finally`) veya yapılandırılmamış özel durum işleme kodu (`On Error GoTo`) ile işleyebileceğiniz bir özel durum oluşturur. `Throw` deyiminizi, uygun özel durum işleme kodunu bulana kadar Visual Basic çağrı yığınını taşıdığından, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.

İfadesi olmayan bir `Throw` deyimi yalnızca bir `Catch` deyiminde kullanılabilir, bu durumda deyim `Catch` deyimi tarafından işlenmekte olan özel durumu yeniden oluşturur.

`Throw` ifade, `expression` özel durumu için çağrı yığınını sıfırlar. `expression` sağlanmazsa, çağrı yığını değişmeden bırakılır. Özel durum için çağrı yığınına <xref:System.Exception.StackTrace%2A> özelliği aracılığıyla erişebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki kod bir özel durum oluşturmak için `Throw` ifadesini kullanır:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
