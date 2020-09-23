---
title: Hatalı kayıt numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 8cbffc7714211fb10bedc3a73729eac59d98f0bb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086991"
---
# <a name="bad-record-number"></a><span data-ttu-id="08ec2-102">Hatalı kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="08ec2-102">Bad record number</span></span>

<span data-ttu-id="08ec2-103">`a FileGet`,, `FilePut` Veya deyimindeki kayıt numarası `FileGetObject` `FilePutObject` sıfıra eşit veya daha az.</span><span class="sxs-lookup"><span data-stu-id="08ec2-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08ec2-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="08ec2-104">To correct this error</span></span>  
  
1. <span data-ttu-id="08ec2-105">Kayıt numarasını oluştururken kullanılan hesaplamaları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="08ec2-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="08ec2-106">Kayıt numarasını içeren veya kayıt numaralarını hesaplamak için kullanılan değişkenlerin yazımını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="08ec2-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="08ec2-107">Yanlış yazılmış bir değişken adı, modülde kullanmadığınız durumlar dışında örtülü olarak belirtilir ve sıfır olarak başlatılır `Option Explicit On` .</span><span class="sxs-lookup"><span data-stu-id="08ec2-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ec2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08ec2-108">See also</span></span>

- [<span data-ttu-id="08ec2-109">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="08ec2-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
