---
title: Tür parametreleri niteleyici olarak kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 14e6094b0cc129eba86db1808c0f0575955f5e75
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161198"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="20718-102">BC32098: tür parametreleri niteleyici olarak kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="20718-102">BC32098: Type parameters cannot be used as qualifiers</span></span>

<span data-ttu-id="20718-103">Bir programlama öğesi, bir tür parametresi içeren bir nitelik dizesi ile nitelenir.</span><span class="sxs-lookup"><span data-stu-id="20718-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>

<span data-ttu-id="20718-104">Bir tür parametresi, genel tür oluşturulduğunda sağlanacak bir tür için bir gereksinimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20718-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="20718-105">Belirli bir tanımlı türü temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="20718-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="20718-106">Bir nitelik dizesinin yalnızca derleme zamanında tanımlanan öğeleri içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="20718-106">A qualification string must include only elements that are defined at compile time.</span></span>

<span data-ttu-id="20718-107">Aşağıdaki kod bu hatayı verebilir:</span><span class="sxs-lookup"><span data-stu-id="20718-107">The following code can generate this error:</span></span>

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 <span data-ttu-id="20718-108">**Hata kimliği:** BC32098</span><span class="sxs-lookup"><span data-stu-id="20718-108">**Error ID:** BC32098</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="20718-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="20718-109">To correct this error</span></span>

1. <span data-ttu-id="20718-110">Nitelik dizesinden tür parametresini kaldırın veya tanımlı bir türle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="20718-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>

2. <span data-ttu-id="20718-111">Nitelenmiş programlama öğesini bulmak için oluşturulmuş bir tür kullanmanız gerekiyorsa ek program mantığını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="20718-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>

## <a name="see-also"></a><span data-ttu-id="20718-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20718-112">See also</span></span>

- [<span data-ttu-id="20718-113">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="20718-113">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="20718-114">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="20718-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="20718-115">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="20718-115">Type List</span></span>](../statements/type-list.md)
