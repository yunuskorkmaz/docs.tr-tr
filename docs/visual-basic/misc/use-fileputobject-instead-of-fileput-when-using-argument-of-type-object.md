---
title: Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725564"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="c354f-102">Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın</span><span class="sxs-lookup"><span data-stu-id="c354f-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="c354f-103">`FilePut` Yöntemi türünde bir bağımsız değişken içeren `Object`.</span><span class="sxs-lookup"><span data-stu-id="c354f-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="c354f-104">`FilePutObject` yerine kullanılması gereken `FilePut` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="c354f-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c354f-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c354f-105">To correct this error</span></span>  
  
-   <span data-ttu-id="c354f-106">`FilePut` yerine `FilePutObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="c354f-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="c354f-107">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c354f-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="c354f-108">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesne.</span><span class="sxs-lookup"><span data-stu-id="c354f-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c354f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c354f-109">See also</span></span>

- [<span data-ttu-id="c354f-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c354f-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="c354f-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="c354f-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
