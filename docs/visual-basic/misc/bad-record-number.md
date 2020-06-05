---
title: Hatalı kayıt numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367548"
---
# <a name="bad-record-number"></a><span data-ttu-id="7ea41-102">Hatalı kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="7ea41-102">Bad record number</span></span>
<span data-ttu-id="7ea41-103">`a FileGet`,, `FilePut` Veya deyimindeki kayıt numarası `FileGetObject` `FilePutObject` sıfıra eşit veya daha az.</span><span class="sxs-lookup"><span data-stu-id="7ea41-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ea41-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7ea41-104">To correct this error</span></span>  
  
1. <span data-ttu-id="7ea41-105">Kayıt numarasını oluştururken kullanılan hesaplamaları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7ea41-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="7ea41-106">Kayıt numarasını içeren veya kayıt numaralarını hesaplamak için kullanılan değişkenlerin yazımını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="7ea41-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="7ea41-107">Yanlış yazılmış bir değişken adı, modülde kullanmadığınız durumlar dışında örtülü olarak belirtilir ve sıfır olarak başlatılır `Option Explicit On` .</span><span class="sxs-lookup"><span data-stu-id="7ea41-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea41-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ea41-108">See also</span></span>

- [<span data-ttu-id="7ea41-109">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="7ea41-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
