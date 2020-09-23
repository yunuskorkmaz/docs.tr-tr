---
title: "' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın"
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 318a0772a99aa86d9a4633e6021f77616a43fc7e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059411"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="5daf9-102">' Object ' türünde bağımsız değişken kullanırken ' FileGet ' yerine ' FileGetObject ' kullanın</span><span class="sxs-lookup"><span data-stu-id="5daf9-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>

<span data-ttu-id="5daf9-103">`FileGet`Yöntemi türünde bir bağımsız değişken içerir `Object` .</span><span class="sxs-lookup"><span data-stu-id="5daf9-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="5daf9-104">`FileGetObject``FileGet`belirsizlikleri kaçınmak için yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5daf9-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="5daf9-105">Tarafından sunulan işlevselliğin, `My.Computer.Filesystem` ya da ' den daha fazla kullanım kolaylığı ve performans sunduğuna dikkat edin `FileGet` `FileGetObject` .</span><span class="sxs-lookup"><span data-stu-id="5daf9-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5daf9-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5daf9-106">To correct this error</span></span>  
  
1. <span data-ttu-id="5daf9-107">`FileGet` yerine `FileGetObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="5daf9-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="5daf9-108">`Object`Bağımsız değişkeni daha belirli bir türe atayın.</span><span class="sxs-lookup"><span data-stu-id="5daf9-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daf9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5daf9-109">See also</span></span>

- [<span data-ttu-id="5daf9-110">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="5daf9-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
