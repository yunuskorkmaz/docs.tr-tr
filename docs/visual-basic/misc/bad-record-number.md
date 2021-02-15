---
description: 'Daha fazla bilgi edinin: Hatalı kayıt numarası'
title: Hatalı kayıt numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: a250419c131f75381426705d52563732322631cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461001"
---
# <a name="bad-record-number"></a><span data-ttu-id="b557a-103">Hatalı kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="b557a-103">Bad record number</span></span>

<span data-ttu-id="b557a-104">`a FileGet`,, `FilePut` Veya deyimindeki kayıt numarası `FileGetObject` `FilePutObject` sıfıra eşit veya daha az.</span><span class="sxs-lookup"><span data-stu-id="b557a-104">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b557a-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b557a-105">To correct this error</span></span>  
  
1. <span data-ttu-id="b557a-106">Kayıt numarasını oluştururken kullanılan hesaplamaları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b557a-106">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="b557a-107">Kayıt numarasını içeren veya kayıt numaralarını hesaplamak için kullanılan değişkenlerin yazımını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b557a-107">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="b557a-108">Yanlış yazılmış bir değişken adı, modülde kullanmadığınız durumlar dışında örtülü olarak belirtilir ve sıfır olarak başlatılır `Option Explicit On` .</span><span class="sxs-lookup"><span data-stu-id="b557a-108">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b557a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b557a-109">See also</span></span>

- [<span data-ttu-id="b557a-110">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="b557a-110">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
