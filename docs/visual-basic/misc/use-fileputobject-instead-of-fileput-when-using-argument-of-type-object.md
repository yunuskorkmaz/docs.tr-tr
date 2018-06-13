---
title: Kullanım &#39;FilePutObject&#39; yerine &#39;FilePut&#39; türünde bağımsız değişken kullanırken &#39;nesnesi&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641134"
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="a9111-102">Kullanım &#39;FilePutObject&#39; yerine &#39;FilePut&#39; türünde bağımsız değişken kullanırken &#39;nesnesi&#39;</span><span class="sxs-lookup"><span data-stu-id="a9111-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="a9111-103">`FilePut` Yöntemi içerir türünde bir bağımsız değişken `Object`.</span><span class="sxs-lookup"><span data-stu-id="a9111-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="a9111-104">`FilePutObject` yerine kullanılmalıdır `FilePut` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="a9111-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a9111-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a9111-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a9111-106">Değiştir `FilePut` ile `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="a9111-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="a9111-107">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a9111-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="a9111-108">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a9111-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9111-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9111-109">See Also</span></span>  
   
 [<span data-ttu-id="a9111-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="a9111-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="a9111-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="a9111-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
