---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
description: Uygulamanızın sınır davranışını veya güvenliğini tanımlamak için ortak salt okuma dizisi alanlarını kullanmaktan kaçının.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 0a6a82c2c88fe61bd34c0accb831f018cf8702fc
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281439"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="d66ac-103">Güvenlik ve Genel Salt Okunur Dizi Alanları</span><span class="sxs-lookup"><span data-stu-id="d66ac-103">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="d66ac-104">Salt okuma genel dizi alanları değiştirilirken, uygulamanızın sınır davranışını veya güvenliğini tanımlamak için, yönetilen kitaplıklardan hiçbir şekilde salt okuma temelli dizi alanları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d66ac-104">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d66ac-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d66ac-105">Remarks</span></span>  

<span data-ttu-id="d66ac-106">Bazı .NET sınıfları, platforma özgü sınır parametreleri içeren salt okunurdur ortak alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="d66ac-106">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="d66ac-107">Örneğin, alan, <xref:System.IO.Path.InvalidPathChars> bir dosya yolu dizesinde izin verilmeyen karakterleri açıklayan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="d66ac-107">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="d66ac-108">Birçok benzer alan .NET genelinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d66ac-108">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="d66ac-109">Gibi genel salt okuma alanlarının değerleri, kodunuzun <xref:System.IO.Path.InvalidPathChars> uygulama etki alanını paylaşan kodunuz veya kodunuz tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d66ac-109">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="d66ac-110">Uygulamalarınızın sınır davranışını tanımlamak için bu gibi salt okunurdur genel dizi alanlarını kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d66ac-110">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="d66ac-111">Bunu yaparsanız, kötü amaçlı kod sınır tanımlarını değiştirebilir ve kodunuzu beklenmedik yollarla kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d66ac-111">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="d66ac-112">Sürüm 2,0 ve .NET Framework üzeri sürümlerde, genel dizi alanlarını kullanmak yerine yeni bir dizi döndüren yöntemleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d66ac-112">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="d66ac-113">Örneğin, alanını kullanmak yerine <xref:System.IO.Path.InvalidPathChars> yöntemini kullanmanız gerekir <xref:System.IO.Path.GetInvalidPathChars%2A> .</span><span class="sxs-lookup"><span data-stu-id="d66ac-113">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="d66ac-114">.NET Framework türlerin, sınır türlerini dahili olarak tanımlamak için ortak alanları kullanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d66ac-114">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="d66ac-115">Bunun yerine, .NET Framework ayrı özel alanlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="d66ac-115">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="d66ac-116">Bu ortak alanların değerlerinin değiştirilmesi .NET Framework türlerinin davranışını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="d66ac-116">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66ac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d66ac-117">See also</span></span>

- [<span data-ttu-id="d66ac-118">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d66ac-118">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
