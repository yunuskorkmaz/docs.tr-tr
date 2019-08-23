---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910731"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="3db7d-102">Güvenlik ve Genel Salt Okunur Dizi Alanları</span><span class="sxs-lookup"><span data-stu-id="3db7d-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="3db7d-103">Salt okuma genel dizi alanları değiştirilirken, uygulamanızın sınır davranışını veya güvenliğini tanımlamak için, yönetilen kitaplıklardan hiçbir şekilde salt okuma temelli dizi alanları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3db7d-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3db7d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3db7d-104">Remarks</span></span>  
 <span data-ttu-id="3db7d-105">Bazı .NET Framework sınıfları, platforma özgü sınır parametreleri içeren salt okunurdur ortak alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="3db7d-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="3db7d-106">Örneğin, <xref:System.IO.Path.InvalidPathChars> alan, bir dosya yolu dizesinde izin verilmeyen karakterleri açıklayan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="3db7d-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="3db7d-107">.NET Framework boyunca birçok benzer alan mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3db7d-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="3db7d-108">Gibi <xref:System.IO.Path.InvalidPathChars> genel salt okuma alanlarının değerleri, kodunuzun uygulama etki alanını paylaşan kodunuz veya kodunuz tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3db7d-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="3db7d-109">Uygulamalarınızın sınır davranışını tanımlamak için bu gibi salt okunurdur genel dizi alanlarını kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3db7d-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="3db7d-110">Bunu yaparsanız, kötü amaçlı kod sınır tanımlarını değiştirebilir ve kodunuzu beklenmedik yollarla kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3db7d-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="3db7d-111">Sürüm 2,0 ve .NET Framework üzeri sürümlerde, genel dizi alanlarını kullanmak yerine yeni bir dizi döndüren yöntemleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3db7d-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="3db7d-112">Örneğin, <xref:System.IO.Path.InvalidPathChars> alanını kullanmak yerine <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3db7d-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="3db7d-113">.NET Framework türlerin, sınır türlerini dahili olarak tanımlamak için ortak alanları kullanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3db7d-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="3db7d-114">Bunun yerine, .NET Framework ayrı özel alanlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="3db7d-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="3db7d-115">Bu ortak alanların değerlerinin değiştirilmesi .NET Framework türlerinin davranışını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="3db7d-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db7d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3db7d-116">See also</span></span>

- [<span data-ttu-id="3db7d-117">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3db7d-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
