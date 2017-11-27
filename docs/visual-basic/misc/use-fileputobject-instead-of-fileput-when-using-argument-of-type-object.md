---
title: "&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="58daf-102">&#39;kullan; FilePutObject &#39; yerine &#39; FilePut &#39; bağımsız değişken türü &#39; nesne &#39;kullanırken;</span><span class="sxs-lookup"><span data-stu-id="58daf-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="58daf-103">`FilePut` Yöntemi içerir türünde bir bağımsız değişken `Object`.</span><span class="sxs-lookup"><span data-stu-id="58daf-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="58daf-104">`FilePutObject`yerine kullanılmalıdır `FilePut` belirsizlikleri önlemek için.</span><span class="sxs-lookup"><span data-stu-id="58daf-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58daf-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="58daf-105">To correct this error</span></span>  
  
-   <span data-ttu-id="58daf-106">Değiştir `FilePut` ile `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="58daf-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="58daf-107">Cast `Object` daha belirli bir tür bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="58daf-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="58daf-108">Kullanılabilir işlevselliği kullanmak `My.Computer.FileSystem` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="58daf-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58daf-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58daf-109">See Also</span></span>  
 [<span data-ttu-id="58daf-110">IN derleme değil: FilePutObject işlevi</span><span class="sxs-lookup"><span data-stu-id="58daf-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="58daf-111">My.Computer.FileSystem nesnesi</span><span class="sxs-lookup"><span data-stu-id="58daf-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="58daf-112">My.Computer.FileSystem.WriteAllBytes yöntemi</span><span class="sxs-lookup"><span data-stu-id="58daf-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
