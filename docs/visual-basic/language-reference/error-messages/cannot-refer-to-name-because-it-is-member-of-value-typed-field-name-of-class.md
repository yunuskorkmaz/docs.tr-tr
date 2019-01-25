---
title: Başvurulamaz &#39; &lt;adı&gt; &#39; değer alanının bir üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfın &#39; &lt;classname&gt; &#39;olduğu &#39;System.MarshalByRefObject&#39; bir temel sınıf olarak
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739303"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="c115c-102">Başvurulamaz &#39; &lt;adı&gt; &#39; değer alanının bir üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfın &#39; &lt;classname&gt; &#39;olduğu &#39;System.MarshalByRefObject&#39; bir temel sınıf olarak</span><span class="sxs-lookup"><span data-stu-id="c115c-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="c115c-103">`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırları uzak nesnelere erişimi destekleyen uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c115c-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="c115c-104">Türleri devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="c115c-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="c115c-105">Bir nesnenin üyelerine oluşturulmuş olan uygulama etki alanı dışında kullanılabilir olmadığı için nesne durumunu kopyalanmayacak.</span><span class="sxs-lookup"><span data-stu-id="c115c-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="c115c-106">**Hata Kimliği:** BC30310</span><span class="sxs-lookup"><span data-stu-id="c115c-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c115c-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c115c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="c115c-108">Başvurulan üyenin geçerli olduğundan emin olmak için başvuru denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c115c-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="c115c-109">Açıkça üyesiyle uygun `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c115c-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c115c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c115c-110">See also</span></span>
- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="c115c-111">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="c115c-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
