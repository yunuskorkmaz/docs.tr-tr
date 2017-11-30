---
title: "Hayır erişilebilir aşırı yüklenmiş &#39; &lt;methodname&gt;&#39; daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 636dbb082323718d8df0371751828e547d99c760
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-overloaded-39ltmethodnamegt39-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="cbc11-102">Hayır erişilebilir aşırı yüklenmiş &#39; &lt;methodname&gt;&#39; daraltma dönüşümü olmadan bu bağımsız değişkenlerle çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="cbc11-102">No accessible overloaded &#39;&lt;methodname&gt;&#39; can be called with these arguments without a narrowing conversion</span></span>
<span data-ttu-id="cbc11-103">Aşırı yüklenmiş yöntemin çağrıldı, ancak hiçbir yöntemi daraltma dönüşümü olmadan sağlanan bağımsız değişkenler listesi ile eşleşen.</span><span class="sxs-lookup"><span data-stu-id="cbc11-103">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbc11-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cbc11-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="cbc11-105">Belirtin `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="cbc11-105">Specify `Option Strict Off`.</span></span>  
  
2.  <span data-ttu-id="cbc11-106">Bağımsız değişkenlerini aşırı yüklenmiş yöntemin imzalarını birini eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cbc11-106">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc11-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbc11-107">See Also</span></span>  
 [<span data-ttu-id="cbc11-108">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="cbc11-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="cbc11-109">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="cbc11-109">Widening and Narrowing Conversions</span></span>](../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
