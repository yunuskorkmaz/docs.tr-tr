---
title: Bağımsız değişken Nothing olamaz
ms.date: 07/20/2015
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
ms.openlocfilehash: 27c959b0fd62a930750bc731e6ca242b2415f1e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087238"
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="46fcf-102">Bağımsız değişken Nothing olamaz</span><span class="sxs-lookup"><span data-stu-id="46fcf-102">Argument cannot be Nothing</span></span>

<span data-ttu-id="46fcf-103">Bir değeri olması gereken bir bağımsız değişken için null değer sağlandı.</span><span class="sxs-lookup"><span data-stu-id="46fcf-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46fcf-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="46fcf-104">To correct this error</span></span>  
  
- <span data-ttu-id="46fcf-105">Nesne örneğini sağlamadan bir nesneyi kullanmayı denemiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46fcf-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="46fcf-106">Böyle bir durumda `New` örneği oluşturmak için anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="46fcf-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
- <span data-ttu-id="46fcf-107">Değerin doğru hesaplanıp hesaplanmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46fcf-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fcf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46fcf-108">See also</span></span>

- <xref:System.NullReferenceException>
