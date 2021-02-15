---
description: "Daha fazla bilgi edinin: <methodname> bir daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz"
title: <methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
ms.openlocfilehash: ff70d43e5e5171055f631a6965b81b934bfb0b39
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479185"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="f0171-103">\<methodname>Daraltma dönüştürmesi olmadan bu bağımsız değişkenlerle hiçbir erişilebilir aşırı yüklü ' ' çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="f0171-103">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion</span></span>

<span data-ttu-id="f0171-104">Aşırı yüklenmiş bir yöntem çağrıldı, ancak bir daraltma dönüştürmesi olmadan belirtilen bağımsız değişkenlerin listesiyle hiçbir yöntem eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="f0171-104">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f0171-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f0171-105">To correct this error</span></span>  
  
1. <span data-ttu-id="f0171-106">`Option Strict Off` belirtin.</span><span class="sxs-lookup"><span data-stu-id="f0171-106">Specify `Option Strict Off`.</span></span>  
  
2. <span data-ttu-id="f0171-107">Bağımsız değişkenleri, aşırı yüklenmiş metodun imzalarından biriyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f0171-107">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0171-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0171-108">See also</span></span>

- [<span data-ttu-id="f0171-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="f0171-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f0171-110">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="f0171-110">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
