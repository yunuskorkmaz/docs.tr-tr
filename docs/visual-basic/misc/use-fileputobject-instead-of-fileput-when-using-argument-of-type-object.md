---
title: "&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="a3978-102">&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;</span><span class="sxs-lookup"><span data-stu-id="a3978-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="a3978-103">`FilePut` Yöntemi içerir türünde bir bağımsız değişken `Object`.</span><span class="sxs-lookup"><span data-stu-id="a3978-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="a3978-104">`FilePutObject`yerine kullanılmalıdır `FilePut` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="a3978-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a3978-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a3978-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a3978-106">Değiştir `FilePut` ile `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="a3978-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="a3978-107">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a3978-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="a3978-108">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a3978-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3978-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3978-109">See Also</span></span>  
   
 [<span data-ttu-id="a3978-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="a3978-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="a3978-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="a3978-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
