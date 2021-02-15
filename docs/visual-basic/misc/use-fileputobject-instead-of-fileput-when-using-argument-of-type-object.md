---
description: "Hakkında daha fazla bilgi edinin: ' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın"
title: "' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 5e5822999aa39bff4d43f83a2719341034cdcadc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460104"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="b67c4-103">' Object ' türünde bağımsız değişken kullanırken ' FilePut ' yerine ' FilePutObject ' kullanın</span><span class="sxs-lookup"><span data-stu-id="b67c4-103">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="b67c4-104">`FilePut`Yöntemi türünde bir bağımsız değişken içerir `Object` .</span><span class="sxs-lookup"><span data-stu-id="b67c4-104">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="b67c4-105">`FilePutObject``FilePut`belirsizlikleri kaçınmak için yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b67c4-105">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b67c4-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b67c4-106">To correct this error</span></span>  
  
- <span data-ttu-id="b67c4-107">`FilePut` yerine `FilePutObject` yazın.</span><span class="sxs-lookup"><span data-stu-id="b67c4-107">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="b67c4-108">`Object`Bağımsız değişkeni daha belirli bir türe atayın.</span><span class="sxs-lookup"><span data-stu-id="b67c4-108">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="b67c4-109">Nesnesinde bulunan işlevleri kullanın `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="b67c4-109">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67c4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b67c4-110">See also</span></span>

- [<span data-ttu-id="b67c4-111">My. Computer. FileSystem</span><span class="sxs-lookup"><span data-stu-id="b67c4-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="b67c4-112">My. Computer. FileSystem. WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="b67c4-112">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
