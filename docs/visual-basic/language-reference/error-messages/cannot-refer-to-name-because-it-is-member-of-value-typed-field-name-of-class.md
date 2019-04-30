---
title: Temel sınıfı 'System.MarshalByRefObject' olan '<name>' sınıfında bulunan değer türündeki '<name>' alanının bir üyesi olduğundan, '<classname>' öğesine başvurulamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: 78b0a3131b6e77ed257f200523ecebd4dfce3691
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649939"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a><span data-ttu-id="f5649-102">Başvurulamaz '\<adı >' değer alanının bir üyesi olduğundan '\<adı >' sınıfının\<SınıfAdı >' temel sınıfı ' System.MarshalByRefObject' olan</span><span class="sxs-lookup"><span data-stu-id="f5649-102">Cannot refer to '\<name>' because it is a member of the value-typed field '\<name>' of class '\<classname>' which has 'System.MarshalByRefObject' as a base class</span></span>
<span data-ttu-id="f5649-103">`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırları uzak nesnelere erişimi destekleyen uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5649-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="f5649-104">Türleri devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="f5649-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="f5649-105">Bir nesnenin üyelerine oluşturulmuş olan uygulama etki alanı dışında kullanılabilir olmadığı için nesne durumunu kopyalanmayacak.</span><span class="sxs-lookup"><span data-stu-id="f5649-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="f5649-106">**Hata Kimliği:** BC30310</span><span class="sxs-lookup"><span data-stu-id="f5649-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5649-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f5649-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f5649-108">Başvurulan üyenin geçerli olduğundan emin olmak için başvuru denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f5649-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2. <span data-ttu-id="f5649-109">Açıkça üyesiyle uygun `Me` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f5649-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5649-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5649-110">See also</span></span>

- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="f5649-111">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="f5649-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
