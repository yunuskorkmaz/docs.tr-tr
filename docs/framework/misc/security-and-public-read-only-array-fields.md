---
title: "Güvenlik ve Genel Salt Okunur Dizi Alanları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d054d3a5a4e10b8efcc3292f3a18ea37f9b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="a5ad0-102">Güvenlik ve Genel Salt Okunur Dizi Alanları</span><span class="sxs-lookup"><span data-stu-id="a5ad0-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="a5ad0-103">Hiçbir zaman genel salt okunur dizi alanları salt okunur genel dizi alanları değiştirilebildiğinden sınır davranışı veya güvenlik uygulamalarınızın tanımlamak için yönetilen kitaplıklarından kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5ad0-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5ad0-104">Remarks</span></span>  
 <span data-ttu-id="a5ad0-105">Bazı .NET framework sınıfları platforma özgü sınır parametreleri içeren salt okunur ortak alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="a5ad0-106">Örneğin, <xref:System.IO.Path.InvalidPathChars> bir dosya yolu dizesinde izin verilmeyen karakterler tanımlayan bir dizi bir alandır.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="a5ad0-107">Pek çok benzer alanları .NET Framework mevcut.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="a5ad0-108">Genel salt okunur alanların değerlerini ister <xref:System.IO.Path.InvalidPathChars> kodu veya paylaşımları, kodun uygulama etki alanı kodu tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="a5ad0-109">Uygulamalarınızı sınır davranışını tanımlamak için bu gibi salt okunur genel dizi alanları kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="a5ad0-110">Bunu yaparsanız, kötü amaçlı kod sınır tanımları alter ve kodunuzu beklenmedik bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="a5ad0-111">Sürüm 2.0 ve daha sonra .NET Framework, genel dizi alanları kullanmak yerine yeni bir dizi döndüren yöntemler kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="a5ad0-112">Örneğin, kullanmak yerine <xref:System.IO.Path.InvalidPathChars> alan, kullanmanız gereken <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="a5ad0-113">.NET Framework türleri genel alanlar sınır türlerinin dahili olarak tanımlamak için kullanmamanızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="a5ad0-114">Bunun yerine, .NET Framework ayrı özel alanları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="a5ad0-115">Bu ortak alanların değerlerini değiştirme .NET Framework türleri davranışını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ad0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5ad0-116">See Also</span></span>  
 [<span data-ttu-id="a5ad0-117">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a5ad0-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
