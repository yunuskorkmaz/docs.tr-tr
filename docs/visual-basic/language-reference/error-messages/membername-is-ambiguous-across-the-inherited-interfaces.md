---
description: "Daha fazla bilgi: BC30685: ' <membername> ', devralınmış ' <interfacename1> ' ve ' arabirimleri arasında belirsiz<interfacename2>"
title: "'<membername>', devralınmış '<interfacename1>' ve '<interfacename2>' arabirimleri arasında belirsiz"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 8d114755c4456c7e846c2e9570481abfd5d13bbf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795839"
---
# <a name="bc30685-membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="afc4b-103">BC30685: ' ' \<membername> , devralınmış ' \<interfacename1> ' ve ' ' arabirimleri arasında belirsiz \<interfacename2></span><span class="sxs-lookup"><span data-stu-id="afc4b-103">BC30685: '\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>

<span data-ttu-id="afc4b-104">Arabirim, birden çok arabirimden aynı ada sahip iki veya daha fazla üyeyi devralır.</span><span class="sxs-lookup"><span data-stu-id="afc4b-104">The interface inherits two or more members with the same name from multiple interfaces.</span></span>

 <span data-ttu-id="afc4b-105">**Hata kimliği:** BC30685</span><span class="sxs-lookup"><span data-stu-id="afc4b-105">**Error ID:** BC30685</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="afc4b-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="afc4b-106">To correct this error</span></span>

- <span data-ttu-id="afc4b-107">Değerini kullanmak istediğiniz temel arabirime atayın; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="afc4b-107">Cast the value to the base interface that you want to use; for example:</span></span>

    ```vb
    Interface Left
        Sub MySub()
    End Interface

    Interface Right
        Sub MySub()
    End Interface

    Interface LeftRight
        Inherits Left, Right
    End Interface

    Module test
        Sub Main()
            Dim x As LeftRight
            ' x.MySub()  'x is ambiguous.
            CType(x, Left).MySub() ' Cast to base type.
            CType(x, Right).MySub() ' Call the other base type.
        End Sub
    End Module
    ```

## <a name="see-also"></a><span data-ttu-id="afc4b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afc4b-108">See also</span></span>

- [<span data-ttu-id="afc4b-109">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="afc4b-109">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
