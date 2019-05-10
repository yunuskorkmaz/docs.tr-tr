---
title: Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: bf1f50d0d8eb9b0b8518075b0e48f40645a02a25
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913221"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="6317a-102">Bağımsız değişken türü 'Object' kullanılırken 'FilePut' yerine 'FilePutObject' kullanın</span><span class="sxs-lookup"><span data-stu-id="6317a-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="6317a-103">`FilePut` Yöntemi türünde bir bağımsız değişken içeren `Object`.</span><span class="sxs-lookup"><span data-stu-id="6317a-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="6317a-104">`FilePutObject` yerine kullanılması gereken `FilePut` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="6317a-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6317a-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6317a-105">To correct this error</span></span>  
  
- <span data-ttu-id="6317a-106">`FilePut` yerine `FilePutObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="6317a-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="6317a-107">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6317a-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="6317a-108">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesne.</span><span class="sxs-lookup"><span data-stu-id="6317a-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6317a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6317a-109">See also</span></span>

- [<span data-ttu-id="6317a-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="6317a-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="6317a-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="6317a-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
