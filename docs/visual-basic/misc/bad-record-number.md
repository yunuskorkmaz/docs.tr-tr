---
title: Hatalı kayıt numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 400879ba37c6b3215d9570ca6eb8eaa06edea03b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600811"
---
# <a name="bad-record-number"></a><span data-ttu-id="55e01-102">Hatalı kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="55e01-102">Bad record number</span></span>
<span data-ttu-id="55e01-103">Kayıt sayısı `a FileGet`, `FilePut`, `FileGetObject`, veya `FilePutObject` açıklamadır sıfıra eşit veya daha az.</span><span class="sxs-lookup"><span data-stu-id="55e01-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="55e01-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="55e01-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="55e01-105">Kayıt sayısı oluşturmak için kullanılan hesaplama denetleyin.</span><span class="sxs-lookup"><span data-stu-id="55e01-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="55e01-106">Kayıt sayısını içeren veya kayıt sayıları hesaplamak için kullanılan değişken yazımını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="55e01-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="55e01-107">Yanlış yazılmış bir değişken adı örtük olarak bildirilen ve kullandığınız sürece, sıfıra başlatıldı `Option Explicit On` modülünde.</span><span class="sxs-lookup"><span data-stu-id="55e01-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e01-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55e01-108">See Also</span></span>  
 [<span data-ttu-id="55e01-109">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="55e01-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
