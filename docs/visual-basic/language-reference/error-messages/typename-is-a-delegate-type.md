---
title: "&#39; &lt;typename&gt;&#39; bir temsilci türü"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="99693-102">&#39; &lt;typename&gt;&#39; bir temsilci türü</span><span class="sxs-lookup"><span data-stu-id="99693-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="99693-103">'\<typename >' temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="99693-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="99693-104">Temsilci yapım yalnızca tek bir AddressOf ifade bir değişken listesi olarak verir.</span><span class="sxs-lookup"><span data-stu-id="99693-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="99693-105">Genellikle bir AddressOf ifade temsilci yapım yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99693-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="99693-106">A `New` yan tümcesi bir temsilci sınıfının bir örneğini oluşturma sağlayan bir temsilci Oluşturucu geçersiz bağımsız değişken listesi.</span><span class="sxs-lookup"><span data-stu-id="99693-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="99693-107">Yalnızca tek bir sağlayabilir `AddressOf` yeni bir temsilci örneği oluşturulurken ifade.</span><span class="sxs-lookup"><span data-stu-id="99693-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="99693-108">Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmek ya da tek bir bağımsız değişken geçirirseniz bir geçerli olmayan geçirmezseniz sonuçlanabilir `AddressOf` ifade.</span><span class="sxs-lookup"><span data-stu-id="99693-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="99693-109">**Hata Kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="99693-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="99693-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="99693-110">To correct this error</span></span>  
  
-   <span data-ttu-id="99693-111">Tek kullanımlık `AddressOf` temsilci sınıfında için bağımsız değişken listesi ifadesinde `New` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="99693-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99693-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99693-112">See Also</span></span>  
 [<span data-ttu-id="99693-113">New işleci</span><span class="sxs-lookup"><span data-stu-id="99693-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="99693-114">AddressOf işleci</span><span class="sxs-lookup"><span data-stu-id="99693-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="99693-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="99693-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="99693-116">Nasıl yapılır: temsilci yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="99693-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
