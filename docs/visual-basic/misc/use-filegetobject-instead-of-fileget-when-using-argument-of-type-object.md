---
title: Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768017"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="4332b-102">Bağımsız değişken türü 'Object' kullanılırken 'FileGet' yerine 'FileGetObject' kullanın</span><span class="sxs-lookup"><span data-stu-id="4332b-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="4332b-103">`FileGet` Yöntemi türünde bir bağımsız değişken içeren `Object`.</span><span class="sxs-lookup"><span data-stu-id="4332b-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="4332b-104">`FileGetObject` yerine kullanılması gereken `FileGet` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="4332b-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="4332b-105">Tarafından sağlanan işlev bildirimi `My.Computer.Filesystem` kullanım ve performans büyük bir kolaylıkla ya da daha sunar `FileGet` veya `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="4332b-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4332b-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4332b-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4332b-107">`FileGet` yerine `FileGetObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="4332b-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="4332b-108">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4332b-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4332b-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4332b-109">See Also</span></span>  
   
 [<span data-ttu-id="4332b-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="4332b-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
