---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;membername&gt; &#39; Arabirimin &#39; &lt;InterfaceName&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574748"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="eb23f-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39; uygulamalıdır &#39; &lt;membername&gt; &#39; Arabirimin &#39; &lt;InterfaceName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="eb23f-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="eb23f-103">'\<typename >' uygulamalıdır '\<membername >' arabirimi için '\<InterfaceName >'.</span><span class="sxs-lookup"><span data-stu-id="eb23f-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="eb23f-104">Uygulama özelliği olmalıdır eşleşen 'ReadOnly' / 'WriteOnly' tanımlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="eb23f-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="eb23f-105">Bir sınıf veya yapı bir arabirim uygulamak talep ancak bir yordam, özellik veya olay arabirim tarafından tanımlanan uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="eb23f-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="eb23f-106">Her arabirimin üyesi uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb23f-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="eb23f-107">**Hata Kimliği:** BC30154</span><span class="sxs-lookup"><span data-stu-id="eb23f-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb23f-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="eb23f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="eb23f-109">Aynı ada ve arabirim içinde tanımlanmış olarak imzaya sahip bir üye bildirir.</span><span class="sxs-lookup"><span data-stu-id="eb23f-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="eb23f-110">Eklediğinizden emin olun en az `End Function`, `End Sub`, veya `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb23f-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="eb23f-111">Ekleme bir `Implements` sonuna yan tümcesi `Function`, `Sub`, `Property`, veya `Event` deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb23f-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="eb23f-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb23f-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="eb23f-113">Bir özellik uygularken emin `ReadOnly` veya `WriteOnly` arabirim tanımı aynı şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb23f-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="eb23f-114">Bir özellik uygularken bildirmek `Get` ve `Set` yordamlar, uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="eb23f-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb23f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb23f-115">See also</span></span>
- [<span data-ttu-id="eb23f-116">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="eb23f-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="eb23f-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="eb23f-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
