---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 04124ca044ad8dbff58f85230d7e10ea336d41e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751702"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="d29e1-102">Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.</span><span class="sxs-lookup"><span data-stu-id="d29e1-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="d29e1-103">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="d29e1-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="d29e1-104">Bir istemci bir özelliği veya yöntemi bir işlem dışı bileşeninin çağrılır ve bir özel nesneye bir başvuru bağımsız değişkenlerden biri geçirilecek çalıştı.</span><span class="sxs-lookup"><span data-stu-id="d29e1-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="d29e1-105">Bir işlem dışı bileşeni, bir geri arama yöntemi, istemci üzerinde çağrılır ve bir özel nesneye bir başvuruya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="d29e1-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="d29e1-106">Bir özel nesneye bir başvuru, yükseltme bir olayın bağımsız değişken olarak geçirmek bir işlem dışı bileşeni çalıştı.</span><span class="sxs-lookup"><span data-stu-id="d29e1-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="d29e1-107">Bir istemci bir özel nesneye başvuru atamayı denediniz bir `ByRef` işleme bir olayının bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d29e1-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d29e1-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d29e1-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d29e1-109">Başvuruyu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d29e1-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29e1-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d29e1-110">See also</span></span>

- [<span data-ttu-id="d29e1-111">Private</span><span class="sxs-lookup"><span data-stu-id="d29e1-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
