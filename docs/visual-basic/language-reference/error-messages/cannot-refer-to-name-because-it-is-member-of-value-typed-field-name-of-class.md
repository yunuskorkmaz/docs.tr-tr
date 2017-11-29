---
title: "Başvuramıyor &#39; &lt;adı&gt;&#39; &#39; değer yazdınız alan üyesi olduğundan&lt; ad&gt;&#39; sınıfı &#39;&lt; ClassName&gt;&#39; olan &#39; System.MarshalByRefObject &#39; bir temel sınıf olarak"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords: BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="cc905-102">Başvuramıyor &#39; &lt;adı&gt;&#39; &#39; değer yazdınız alan üyesi olduğundan&lt; ad&gt;&#39; sınıfı &#39;&lt; ClassName&gt;&#39; olan &#39; System.MarshalByRefObject &#39; bir temel sınıf olarak</span><span class="sxs-lookup"><span data-stu-id="cc905-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="cc905-103">`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırlarında nesnelere uzaktan erişimi destekleyen uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc905-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="cc905-104">Türleri öğesinden devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="cc905-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="cc905-105">Nesne üyeleri oluşturulmuş uygulama etki alanı kullanılabilir olmadığından nesnenin durumunu kopyalanmayacak.</span><span class="sxs-lookup"><span data-stu-id="cc905-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="cc905-106">**Hata Kimliği:** BC30310</span><span class="sxs-lookup"><span data-stu-id="cc905-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc905-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cc905-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc905-108">Başvurulan üye geçerli olduğundan emin olmak için başvuru denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cc905-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="cc905-109">Açıkça üyesiyle nitelemek `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="cc905-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc905-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc905-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="cc905-111">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="cc905-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
