---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03f3ce51eaab9e08d5f05932d9360adc4fd2110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560999"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="df5e8-102">Güvenlik ve Genel Salt Okunur Dizi Alanları</span><span class="sxs-lookup"><span data-stu-id="df5e8-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="df5e8-103">Hiçbir zaman salt okunur genel dizi alanları salt okunur genel dizi alanları değiştirilebilir uygulamalarınızın güvenliği ve sınır davranışını tanımlamak için yönetilen kitaplıklarından kullanın.</span><span class="sxs-lookup"><span data-stu-id="df5e8-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df5e8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df5e8-104">Remarks</span></span>  
 <span data-ttu-id="df5e8-105">Bazı .NET framework sınıfları, platforma özgü sınır parametreleri içeren salt okunur ortak alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="df5e8-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="df5e8-106">Örneğin, <xref:System.IO.Path.InvalidPathChars> dosya yol dizesi izin verilmeyen karakterler tanımlayan bir dizi bir alandır.</span><span class="sxs-lookup"><span data-stu-id="df5e8-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="df5e8-107">Pek çok benzer alanları, .NET Framework'de yok.</span><span class="sxs-lookup"><span data-stu-id="df5e8-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="df5e8-108">Genel salt okunur alanların değerlerini ister <xref:System.IO.Path.InvalidPathChars> kodunuzu veya kodunuzun uygulama etki alanını paylaşan kod tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="df5e8-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="df5e8-109">Uygulamalarınızı sınır davranışını tanımlamak için salt okunur genel dizi alanları böyle kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df5e8-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="df5e8-110">Bunu yaparsanız, kötü amaçlı kod sınır tanımları alter ve kodunuzu beklenmedik bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="df5e8-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="df5e8-111">Sürüm 2.0 ve daha sonra .NET Framework, ortak bir dizi alanları kullanmak yerine yeni bir dizi döndüren yöntemler kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="df5e8-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="df5e8-112">Örneğin, kullanmak yerine <xref:System.IO.Path.InvalidPathChars> alan kullanmalıdır <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df5e8-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="df5e8-113">.NET Framework türleri genel alanlar dahili olarak sınır türleri tanımlamak için kullanmamanız unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df5e8-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="df5e8-114">Bunun yerine, .NET Framework ayrı özel alanları kullanır.</span><span class="sxs-lookup"><span data-stu-id="df5e8-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="df5e8-115">Bu genel alanların değerlerini değiştirme, .NET Framework türleri davranışını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="df5e8-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5e8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df5e8-116">See also</span></span>
- [<span data-ttu-id="df5e8-117">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="df5e8-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
