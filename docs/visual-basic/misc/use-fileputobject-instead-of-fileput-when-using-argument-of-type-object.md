---
title: "' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100340"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="8b64a-102">' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın</span><span class="sxs-lookup"><span data-stu-id="8b64a-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="8b64a-103">`FilePut`Yöntemi türünde bir bağımsız değişken içerir `Object` .</span><span class="sxs-lookup"><span data-stu-id="8b64a-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="8b64a-104">`FilePutObject``FilePut`belirsizlikleri kaçınmak için yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b64a-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8b64a-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8b64a-105">To correct this error</span></span>  
  
- <span data-ttu-id="8b64a-106">`FilePut` yerine `FilePutObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="8b64a-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="8b64a-107">`Object`Bağımsız değişkeni daha belirli bir türe atayın.</span><span class="sxs-lookup"><span data-stu-id="8b64a-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="8b64a-108">Nesnesinde bulunan işlevleri kullanın `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="8b64a-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b64a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b64a-109">See also</span></span>

- [<span data-ttu-id="8b64a-110">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="8b64a-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="8b64a-111">My. Computer. FileSystem. WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="8b64a-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
