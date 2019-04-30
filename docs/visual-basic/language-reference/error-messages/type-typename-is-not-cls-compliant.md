---
title: <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 243f51b3e6c798c82fdbe7b28557c4f96c728bf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764380"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="ce3ed-102">Tür \<typename > CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="ce3ed-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="ce3ed-103">Bir değişken, özellik veya işlev dönüş CLS uyumlu olmayan bir veri türü ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="ce3ed-104">Bir uygulama ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), yalnızca CLS uyumlu türler kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="ce3ed-105">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="ce3ed-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="ce3ed-106">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ce3ed-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="ce3ed-107">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ce3ed-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="ce3ed-108">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ce3ed-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="ce3ed-109">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ce3ed-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="ce3ed-110">**Hata Kimliği:** BC40041</span><span class="sxs-lookup"><span data-stu-id="ce3ed-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ce3ed-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ce3ed-111">To correct this error</span></span>  
  
- <span data-ttu-id="ce3ed-112">Uygulamanızı CLS uyumlu olması gerekiyorsa, bu öğe veri türü en yakın CLS uyumlu türüne değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="ce3ed-113">Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="ce3ed-114">Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="ce3ed-115">Uygulamanızı CLS uyumlu olması gerekmez, herhangi bir ayarı değiştirmek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="ce3ed-116">Ancak, uyumsuzluk farkında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce3ed-116">You should be aware of its noncompliance, however.</span></span>