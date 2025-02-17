---
description: 'Daha fazla bilgi edinin: throw deyimleri (Visual Basic)'
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
ms.openlocfilehash: b7fa4183b5997e5dac8045502a8eed1afe66fc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740944"
---
# <a name="throw-statement-visual-basic"></a>Throw Deyimi (Visual Basic)

Bir yordam içinde özel durum oluşturur.

## <a name="syntax"></a>Syntax

```vb
Throw [ expression ]
```

## <a name="part"></a>Bölüm

`expression`\
Oluşturulacak özel durum hakkında bilgi sağlar. Bir bildirimde bulunduğunda isteğe bağlı `Catch` , aksi takdirde gereklidir.

## <a name="remarks"></a>Açıklamalar

`Throw`Bu ifade, yapılandırılmış özel durum işleme kodu ( `Try` ... `Catch` ) ile işleyebileceğiniz bir özel durum oluşturur. ...`Finally`) ya da yapılandırılmamış özel durum işleme kodu ( `On Error GoTo` ). `Throw`Bu ifadeyi, uygun özel durum işleme kodunu bulana kadar çağrı yığınını Visual Basic, kodunuzun içindeki hataları yakalamak için kullanabilirsiniz.

`Throw`İfadesi olmayan bir deyim yalnızca bir `Catch` deyimde kullanılabilir, bu durumda deyim deyim tarafından işlenmekte olan özel durumu yeniden oluşturur `Catch` .

`Throw`İfade, özel durum için çağrı yığınını sıfırlar `expression` . `expression`Sağlanmazsa, çağrı yığını değişmeden bırakılır. Özel durum için çağrı yığınına özelliği aracılığıyla erişebilirsiniz <xref:System.Exception.StackTrace%2A> .

## <a name="example"></a>Örnek

Aşağıdaki kod `Throw` bir özel durum oluşturmak için ifadesini kullanır:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
- [On Error Deyimi](on-error-statement.md)
