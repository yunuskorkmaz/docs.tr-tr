---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250148"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="829c9-102">Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez</span><span class="sxs-lookup"><span data-stu-id="829c9-102">Arrays declared as structure members cannot be declared with an initial size</span></span>

<span data-ttu-id="829c9-103">Yapıdaki bir dizi, başlangıç boyutuyla birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="829c9-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="829c9-104">Herhangi bir yapı öğesini başlatamıyor ve bir dizi boyutunun bildirilmesi, tek bir başlatma biçimidir.</span><span class="sxs-lookup"><span data-stu-id="829c9-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>

<span data-ttu-id="829c9-105">**Hata kimliği:** BC31043</span><span class="sxs-lookup"><span data-stu-id="829c9-105">**Error ID:** BC31043</span></span>

## <a name="example"></a><span data-ttu-id="829c9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="829c9-106">Example</span></span>

<span data-ttu-id="829c9-107">Aşağıdaki örnek BC31043 oluşturur:</span><span class="sxs-lookup"><span data-stu-id="829c9-107">The following example generates BC31043:</span></span>

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a><span data-ttu-id="829c9-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="829c9-108">To correct this error</span></span>

1. <span data-ttu-id="829c9-109">Yapıdaki diziyi dinamik (başlangıç boyutu olmadan) olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="829c9-109">Define the array in your structure as dynamic (no initial size).</span></span>

2. <span data-ttu-id="829c9-110">Belirli bir dizi boyutuna ihtiyacınız varsa, kodunuz çalışırken bir [ReDim ifadesiyle](../statements/redim-statement.md) dinamik bir diziyi yeniden Dimension uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="829c9-110">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="829c9-111">Aşağıdaki örnek şunu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="829c9-111">The following example illustrates this:</span></span>
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a><span data-ttu-id="829c9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="829c9-112">See also</span></span>

- [<span data-ttu-id="829c9-113">Diziler</span><span class="sxs-lookup"><span data-stu-id="829c9-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="829c9-114">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="829c9-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
