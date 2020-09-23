---
title: <methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
ms.openlocfilehash: 1bfa2b508e7102c6d1a3ea9279819d74d478a640
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077507"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="b19f6-102">\<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="b19f6-102">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion</span></span>

<span data-ttu-id="b19f6-103">Aşırı yüklenmiş bir yöntem çağrıldı, ancak bir daraltma dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle hiçbir yöntem eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="b19f6-103">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b19f6-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b19f6-104">To correct this error</span></span>  
  
1. <span data-ttu-id="b19f6-105">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="b19f6-105">Specify `Option Strict Off`.</span></span>  
  
2. <span data-ttu-id="b19f6-106">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzalarından biriyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b19f6-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19f6-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b19f6-107">See also</span></span>

- [<span data-ttu-id="b19f6-108">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="b19f6-108">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="b19f6-109">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b19f6-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
