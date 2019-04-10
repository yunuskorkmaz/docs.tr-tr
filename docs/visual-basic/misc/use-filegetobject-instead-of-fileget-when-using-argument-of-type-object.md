---
title: Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: fdad64a4b35aa792c996d25a9fd72a9ce1126fbd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306930"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="c2031-102">Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın</span><span class="sxs-lookup"><span data-stu-id="c2031-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="c2031-103">`FileGet` Yöntemi türünde bir bağımsız değişken içeren `Object`.</span><span class="sxs-lookup"><span data-stu-id="c2031-103">The `FileGet` method includes an argument of type `Object`.</span></span> `FileGetObject` <span data-ttu-id="c2031-104">yerine kullanılması gereken `FileGet` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="c2031-104">should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="c2031-105">Tarafından sağlanan işlev bildirimi `My.Computer.Filesystem` kullanım ve performans büyük bir kolaylıkla ya da daha sunar `FileGet` veya `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c2031-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2031-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c2031-106">To correct this error</span></span>  
  
1. <span data-ttu-id="c2031-107">`FileGet` yerine `FileGetObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="c2031-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2. <span data-ttu-id="c2031-108">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c2031-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2031-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2031-109">See also</span></span>

- [<span data-ttu-id="c2031-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c2031-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
