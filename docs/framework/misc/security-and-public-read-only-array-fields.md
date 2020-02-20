---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452714"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="2a77f-102">Güvenlik ve Genel Salt Okunur Dizi Alanları</span><span class="sxs-lookup"><span data-stu-id="2a77f-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="2a77f-103">Salt okuma genel dizi alanları değiştirilirken, uygulamanızın sınır davranışını veya güvenliğini tanımlamak için, yönetilen kitaplıklardan hiçbir şekilde salt okuma temelli dizi alanları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2a77f-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a77f-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a77f-104">Remarks</span></span>  

<span data-ttu-id="2a77f-105">Bazı .NET sınıfları, platforma özgü sınır parametreleri içeren salt okunurdur ortak alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-105">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="2a77f-106">Örneğin, <xref:System.IO.Path.InvalidPathChars> alanı bir dosya yolu dizesinde izin verilmeyen karakterleri açıklayan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="2a77f-107">Birçok benzer alan .NET genelinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2a77f-107">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="2a77f-108"><xref:System.IO.Path.InvalidPathChars> gibi genel salt okuma alanlarının değerleri, kodunuzun uygulama etki alanını paylaşan kodunuz veya kodunuz tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="2a77f-109">Uygulamalarınızın sınır davranışını tanımlamak için bu gibi salt okunurdur genel dizi alanlarını kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2a77f-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="2a77f-110">Bunu yaparsanız, kötü amaçlı kod sınır tanımlarını değiştirebilir ve kodunuzu beklenmedik yollarla kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="2a77f-111">Sürüm 2,0 ve .NET Framework üzeri sürümlerde, genel dizi alanlarını kullanmak yerine yeni bir dizi döndüren yöntemleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="2a77f-112">Örneğin, <xref:System.IO.Path.InvalidPathChars> alanı kullanmak yerine <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="2a77f-113">.NET Framework türlerin, sınır türlerini dahili olarak tanımlamak için ortak alanları kullanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2a77f-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="2a77f-114">Bunun yerine, .NET Framework ayrı özel alanlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a77f-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="2a77f-115">Bu ortak alanların değerlerinin değiştirilmesi .NET Framework türlerinin davranışını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="2a77f-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a77f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a77f-116">See also</span></span>

- [<span data-ttu-id="2a77f-117">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2a77f-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
