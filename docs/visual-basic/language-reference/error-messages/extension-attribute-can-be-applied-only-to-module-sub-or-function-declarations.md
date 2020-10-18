---
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: bd4d14721b93800831dbce897535b4f5956fe9c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160756"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>BC36550: ' Extension ' özniteliği yalnızca ' Module ', ' Sub ' veya ' function ' bildirimlerine uygulanabilir

Visual Basic bir veri türünü genişletmenin tek yolu standart bir modül içinde bir genişletme yöntemi tanımlamaktır. Genişletme yöntemi bir `Sub` yordam veya `Function` yordam olabilir. Tüm genişletme yöntemleri, ad alanından uzantı özniteliğiyle işaretlenmelidir `<Extension()>` <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> . İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenebilir. Uzantı özniteliğinin başka bir kullanımı geçerli değil.

**Hata kimliği:** BC36550

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Uzantı özniteliğini kaldırın.

- Uzantınızı bir kapsayıcı modülünde tanımlanan bir yöntem olarak yeniden tasarlama.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Print` veri türü için bir yöntemi tanımlar `String` .

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>Ayrıca bkz.

- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
- [Uzantı Metotları](../../programming-guide/language-features/procedures/extension-methods.md)
- [Module Deyimi](../statements/module-statement.md)
