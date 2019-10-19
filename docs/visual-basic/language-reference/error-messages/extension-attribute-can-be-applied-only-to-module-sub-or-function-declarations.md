---
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583178"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="b48a9-102">'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir</span><span class="sxs-lookup"><span data-stu-id="b48a9-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="b48a9-103">Visual Basic bir veri türünü genişletmenin tek yolu standart bir modül içinde bir genişletme yöntemi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b48a9-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="b48a9-104">Genişletme yöntemi bir `Sub` yordamı veya bir `Function` yordamı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b48a9-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="b48a9-105">Tüm genişletme yöntemlerinin, <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanından `<Extension()>` uzantı özniteliğiyle işaretlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b48a9-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b48a9-106">İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b48a9-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="b48a9-107">Uzantı özniteliğinin başka bir kullanımı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b48a9-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="b48a9-108">**Hata kimliği:** BC36550</span><span class="sxs-lookup"><span data-stu-id="b48a9-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b48a9-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b48a9-109">To correct this error</span></span>

- <span data-ttu-id="b48a9-110">Uzantı özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b48a9-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="b48a9-111">Uzantınızı bir kapsayıcı modülünde tanımlanan bir yöntem olarak yeniden tasarlama.</span><span class="sxs-lookup"><span data-stu-id="b48a9-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="b48a9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b48a9-112">Example</span></span>

<span data-ttu-id="b48a9-113">Aşağıdaki örnek, `String` veri türü için bir `Print` yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b48a9-113">The following example defines a `Print` method for the `String` data type.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b48a9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b48a9-114">See also</span></span>

- [<span data-ttu-id="b48a9-115">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="b48a9-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b48a9-116">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b48a9-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="b48a9-117">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="b48a9-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
