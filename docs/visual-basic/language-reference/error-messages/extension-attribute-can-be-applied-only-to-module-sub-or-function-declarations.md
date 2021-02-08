---
description: "Hakkında daha fazla bilgi edinin: BC36550: ' Extension ' özniteliği yalnızca ' Module ', ' Sub ' veya ' function ' bildirimlerine uygulanabilir"
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: f0c87de34238974229bc572a0f634a16e8cc78d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796320"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="7a6b5-103">BC36550: ' Extension ' özniteliği yalnızca ' Module ', ' Sub ' veya ' function ' bildirimlerine uygulanabilir</span><span class="sxs-lookup"><span data-stu-id="7a6b5-103">BC36550: 'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="7a6b5-104">Visual Basic bir veri türünü genişletmenin tek yolu standart bir modül içinde bir genişletme yöntemi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-104">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="7a6b5-105">Genişletme yöntemi bir `Sub` yordam veya `Function` yordam olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-105">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="7a6b5-106">Tüm genişletme yöntemleri, ad alanından uzantı özniteliğiyle işaretlenmelidir `<Extension()>` <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7a6b5-106">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7a6b5-107">İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-107">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="7a6b5-108">Uzantı özniteliğinin başka bir kullanımı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-108">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="7a6b5-109">**Hata kimliği:** BC36550</span><span class="sxs-lookup"><span data-stu-id="7a6b5-109">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7a6b5-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7a6b5-110">To correct this error</span></span>

- <span data-ttu-id="7a6b5-111">Uzantı özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-111">Remove the extension attribute.</span></span>

- <span data-ttu-id="7a6b5-112">Uzantınızı bir kapsayıcı modülünde tanımlanan bir yöntem olarak yeniden tasarlama.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-112">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="7a6b5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a6b5-113">Example</span></span>

<span data-ttu-id="7a6b5-114">Aşağıdaki örnek, `Print` veri türü için bir yöntemi tanımlar `String` .</span><span class="sxs-lookup"><span data-stu-id="7a6b5-114">The following example defines a `Print` method for the `String` data type.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7a6b5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a6b5-115">See also</span></span>

- [<span data-ttu-id="7a6b5-116">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="7a6b5-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="7a6b5-117">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="7a6b5-117">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="7a6b5-118">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="7a6b5-118">Module Statement</span></span>](../statements/module-statement.md)
