---
title: Tür &lt;typename&gt; CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 9911b4fe7b88996f17cb5e9eec7d4a5f2c254b76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594614"
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="a78a0-102">Tür &lt;typename&gt; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="a78a0-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="a78a0-103">Değişken, özellik veya işlev dönüş CLS ile uyumlu olmayan bir veri türüyle bildirildi.</span><span class="sxs-lookup"><span data-stu-id="a78a0-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="a78a0-104">Bir uygulama ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a78a0-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="a78a0-105">Aşağıdaki Visual Basic veri türleri CLS uyumlu değil:</span><span class="sxs-lookup"><span data-stu-id="a78a0-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="a78a0-106">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a78a0-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="a78a0-107">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a78a0-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="a78a0-108">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a78a0-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="a78a0-109">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a78a0-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="a78a0-110">**Hata Kimliği:** BC40041</span><span class="sxs-lookup"><span data-stu-id="a78a0-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a78a0-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a78a0-111">To correct this error</span></span>  
  
-   <span data-ttu-id="a78a0-112">Uygulamanızı CLS ile uyumlu olması gerekiyorsa, bu öğenin veri türü için en yakın CLS uyumlu türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a78a0-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="a78a0-113">Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="a78a0-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="a78a0-114">Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="a78a0-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="a78a0-115">Uygulamanızı CLS ile uyumlu olması gerekmez, değişikliği gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a78a0-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="a78a0-116">Ancak kendi uyumsuzluğunu, farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a78a0-116">You should be aware of its noncompliance, however.</span></span>