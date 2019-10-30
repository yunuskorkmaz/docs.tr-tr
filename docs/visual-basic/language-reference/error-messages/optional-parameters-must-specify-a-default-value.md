---
title: İsteğe bağlı parametreler varsayılan bir değer belirtmelidir
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040936"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="86aa6-102">İsteğe bağlı parametreler varsayılan bir değer belirtmelidir</span><span class="sxs-lookup"><span data-stu-id="86aa6-102">Optional parameters must specify a default value</span></span>

<span data-ttu-id="86aa6-103">İsteğe bağlı parametreler, bir çağıran yordam tarafından hiçbir parametre sağlanmadığında kullanılabilecek varsayılan değerler sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="86aa6-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="86aa6-104">**Hata kimliği:** BC30812</span><span class="sxs-lookup"><span data-stu-id="86aa6-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="86aa6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="86aa6-105">Example</span></span>

<span data-ttu-id="86aa6-106">Aşağıdaki örnek BC30812 oluşturur:</span><span class="sxs-lookup"><span data-stu-id="86aa6-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="86aa6-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="86aa6-107">To correct this error</span></span>

<span data-ttu-id="86aa6-108">İsteğe bağlı parametreler için varsayılan değerleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="86aa6-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="86aa6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86aa6-109">See also</span></span>

- [<span data-ttu-id="86aa6-110">Optional</span><span class="sxs-lookup"><span data-stu-id="86aa6-110">Optional</span></span>](../modifiers/optional.md)
