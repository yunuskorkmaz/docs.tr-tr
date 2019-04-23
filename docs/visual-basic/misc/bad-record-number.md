---
title: Geçersiz kayıt numarası
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: abd0a1467c0991a40b93e74a1d7a7889367fb8ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340808"
---
# <a name="bad-record-number"></a><span data-ttu-id="0afaf-102">Geçersiz kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="0afaf-102">Bad record number</span></span>
<span data-ttu-id="0afaf-103">Kayıt numarası `a FileGet`, `FilePut`, `FileGetObject`, veya `FilePutObject` deyimdir sıfırdan küçüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="0afaf-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0afaf-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0afaf-104">To correct this error</span></span>  
  
1. <span data-ttu-id="0afaf-105">Kayıt sayısı oluşturmak için kullanılan hesaplama denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0afaf-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="0afaf-106">Kayıt numarası içeren veya kayıt sayıları hesaplamak için kullanılan değişkenleri yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0afaf-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="0afaf-107">Yanlış yazılmış bir değişken adı örtük olarak bildirilmiş ve kullandığınız sürece sıfır olarak başlatılır `Option Explicit On` modülünde.</span><span class="sxs-lookup"><span data-stu-id="0afaf-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0afaf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0afaf-108">See also</span></span>

- [<span data-ttu-id="0afaf-109">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="0afaf-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
