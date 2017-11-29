---
title: "Oluşturucu &#39; &lt;adı&gt;&#39; kendisini çağıramaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords: BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="c1c84-102">Oluşturucu &#39; &lt;adı&gt;&#39; kendisini çağıramaz</span><span class="sxs-lookup"><span data-stu-id="c1c84-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="c1c84-103">A `Sub New` bir sınıf veya yapı yordamda kendisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c1c84-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="c1c84-104">Sınıfının bir örneği başlatmak için bir oluşturucu amacı olan veya ilk çalıştırıldığında yapısı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c1c84-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="c1c84-105">Hepsi farklı parametre listeniz sağlanan birkaç Oluşturucusu bir sınıf veya yapı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1c84-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="c1c84-106">Bir oluşturucu yanı sıra kendi işlevlerini gerçekleştirmek için başka bir oluşturucuyu çağırmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c1c84-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="c1c84-107">Ancak bir oluşturucu kendisini çağırmak anlamsız ve aslında bu içinde sonsuz özyineleme izin veriyorsa, neden olur.</span><span class="sxs-lookup"><span data-stu-id="c1c84-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="c1c84-108">**Hata Kimliği:** BC30298</span><span class="sxs-lookup"><span data-stu-id="c1c84-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c1c84-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c1c84-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="c1c84-110">Çağrılan Oluşturucusu parametre listesini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="c1c84-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="c1c84-111">Çağrıyı yapan Oluşturucusu farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1c84-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="c1c84-112">Farklı bir oluşturucu çağırmak düşünmüyorsanız kaldırmak `Sub New` tamamen çağırın.</span><span class="sxs-lookup"><span data-stu-id="c1c84-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c84-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1c84-113">See Also</span></span>  
 [<span data-ttu-id="c1c84-114">Nesne ömrü: Nesneleri oluşturma ve yok etme</span><span class="sxs-lookup"><span data-stu-id="c1c84-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
