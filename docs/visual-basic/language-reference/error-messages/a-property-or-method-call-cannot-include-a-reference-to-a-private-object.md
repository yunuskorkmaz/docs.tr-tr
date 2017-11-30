---
title: "Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="454eb-102">Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.</span><span class="sxs-lookup"><span data-stu-id="454eb-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="454eb-103">Bu hatanın olası nedenleri arasında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="454eb-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="454eb-104">Bir istemci bir özelliği veya yöntemi bir işlem dışı bileşen çağrılır ve özel bir nesneye başvuru bağımsız değişkenlerden biri geçirme girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="454eb-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="454eb-105">Bir işlem dışı bileşen, istemci üzerinde geri arama yöntemi çağrılır ve özel bir nesneye başvuru geçirme girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="454eb-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="454eb-106">Özel bir nesneye başvuru oluşturma bir olay bağımsız değişken olarak geçirmek bir işlem dışı bileşen çalıştı.</span><span class="sxs-lookup"><span data-stu-id="454eb-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="454eb-107">Bir özel nesneye başvuru atamak bir istemci çalıştı bir `ByRef` işleme olayının bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="454eb-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="454eb-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="454eb-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="454eb-109">Başvurusunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="454eb-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454eb-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="454eb-110">See Also</span></span>  
 [<span data-ttu-id="454eb-111">Özel</span><span class="sxs-lookup"><span data-stu-id="454eb-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
