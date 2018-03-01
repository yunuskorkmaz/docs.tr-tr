---
title: "Bağımsız değişken Nothing olamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5de506c4a24f787dbb9e2d96f0e9e228f7e92288
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="a8b93-102">Bağımsız değişken Nothing olamaz</span><span class="sxs-lookup"><span data-stu-id="a8b93-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="a8b93-103">Bir null değer bir değere sahip olması gereken bir bağımsız değişken belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="a8b93-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8b93-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a8b93-104">To correct this error</span></span>  
  
-   <span data-ttu-id="a8b93-105">Nesne örneği sağlamadan nesneyi kullanmaya çalışmış.</span><span class="sxs-lookup"><span data-stu-id="a8b93-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="a8b93-106">Böyle bir durumda kullanmak `New` örneği oluşturmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a8b93-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="a8b93-107">Değer doğru hesaplanır denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a8b93-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b93-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8b93-108">See Also</span></span>  
 <xref:System.NullReferenceException>
