---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583831"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="c09e0-102">Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.</span><span class="sxs-lookup"><span data-stu-id="c09e0-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="c09e0-103">Bu hatanın olası nedenleri arasında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c09e0-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="c09e0-104">Bir istemci bir özelliği veya yöntemi bir işlem dışı bileşen çağrılır ve özel bir nesneye başvuru bağımsız değişkenlerden biri geçirme girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="c09e0-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="c09e0-105">Bir işlem dışı bileşen, istemci üzerinde geri arama yöntemi çağrılır ve özel bir nesneye başvuru geçirme girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="c09e0-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="c09e0-106">Özel bir nesneye başvuru oluşturma bir olay bağımsız değişken olarak geçirmek bir işlem dışı bileşen çalıştı.</span><span class="sxs-lookup"><span data-stu-id="c09e0-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="c09e0-107">Bir özel nesneye başvuru atamak bir istemci çalıştı bir `ByRef` işleme olayının bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c09e0-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c09e0-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c09e0-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c09e0-109">Başvurusunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c09e0-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09e0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c09e0-110">See Also</span></span>  
 [<span data-ttu-id="c09e0-111">Private</span><span class="sxs-lookup"><span data-stu-id="c09e0-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
