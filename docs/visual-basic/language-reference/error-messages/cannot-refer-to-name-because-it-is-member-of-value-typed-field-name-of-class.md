---
title: Başvuramıyor &#39; &lt;adı&gt; &#39; değer yazdınız alanın üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfının &#39; &lt;classname&gt; &#39;olan &#39;System.MarshalByRefObject&#39; temel sınıf olarak
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586353"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="74609-102">Başvuramıyor &#39; &lt;adı&gt; &#39; değer yazdınız alanın üyesi olduğundan &#39; &lt;adı&gt; &#39; sınıfının &#39; &lt;classname&gt; &#39;olan &#39;System.MarshalByRefObject&#39; temel sınıf olarak</span><span class="sxs-lookup"><span data-stu-id="74609-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="74609-103">`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırlarında nesnelere uzaktan erişimi destekleyen uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="74609-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="74609-104">Türleri öğesinden devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="74609-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="74609-105">Nesne üyeleri oluşturulmuş uygulama etki alanı kullanılabilir olmadığından nesnenin durumunu kopyalanmayacak.</span><span class="sxs-lookup"><span data-stu-id="74609-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="74609-106">**Hata Kimliği:** BC30310</span><span class="sxs-lookup"><span data-stu-id="74609-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74609-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="74609-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="74609-108">Başvurulan üye geçerli olduğundan emin olmak için başvuru denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74609-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="74609-109">Açıkça üyesiyle nitelemek `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="74609-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74609-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74609-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="74609-111">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="74609-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
