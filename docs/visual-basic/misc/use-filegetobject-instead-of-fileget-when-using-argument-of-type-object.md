---
description: "Hakkında daha fazla bilgi edinin: ' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın"
title: "' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 4481fdced961cacf0e652c141601efa13bec776b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471168"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="0716f-103">' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın</span><span class="sxs-lookup"><span data-stu-id="0716f-103">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>

<span data-ttu-id="0716f-104">`FileGet`Yöntemi türünde bir bağımsız değişken içerir `Object` .</span><span class="sxs-lookup"><span data-stu-id="0716f-104">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="0716f-105">`FileGetObject``FileGet`belirsizlikleri kaçınmak için yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0716f-105">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="0716f-106">Tarafından sunulan işlevselliğin, `My.Computer.Filesystem` ya da ' den daha fazla kullanım kolaylığı ve performans sunduğuna dikkat edin `FileGet` `FileGetObject` .</span><span class="sxs-lookup"><span data-stu-id="0716f-106">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0716f-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0716f-107">To correct this error</span></span>  
  
1. <span data-ttu-id="0716f-108">`FileGet` yerine `FileGetObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="0716f-108">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="0716f-109">`Object`Bağımsız değişkeni daha belirli bir türe atayın.</span><span class="sxs-lookup"><span data-stu-id="0716f-109">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0716f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0716f-110">See also</span></span>

- [<span data-ttu-id="0716f-111">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="0716f-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
