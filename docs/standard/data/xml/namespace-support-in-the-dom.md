---
title: "DOM Namespace desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b8135a55c537f480e0d595e127c2cad55e977ca
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="010ad-102">DOM Namespace desteği</span><span class="sxs-lookup"><span data-stu-id="010ad-102">Namespace Support in the DOM</span></span>
<span data-ttu-id="010ad-103">XML belge nesne modeli (DOM) ad alanı tamamen uyumlu.</span><span class="sxs-lookup"><span data-stu-id="010ad-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="010ad-104">Yalnızca ad alanı algılayan XML belgelerini desteklenir.</span><span class="sxs-lookup"><span data-stu-id="010ad-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="010ad-105">World Wide Web Konsorsiyumu (W3C) Düzey 1 uygulamak DOM uygulamaları ad alanı kullanmayan olabilir ve DOM Düzey 2 özellikleri ad alanı algılayan belirtir.</span><span class="sxs-lookup"><span data-stu-id="010ad-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="010ad-106">Ancak, XML DOM'ındaki tüm özelliklere ad alanı algılayan, yöntem düzey 1 veya Düzey 2 DOM öneri ise bakılmaksızın değildir.</span><span class="sxs-lookup"><span data-stu-id="010ad-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="010ad-107">Örneğin, bir ad alanı kullanmayan ayarı içinde çağırma `setAttribute("A:b", "123")`, düzey 1 öneri DOM belirtildiği gibi bir öznitelikte öneki olan sonuçlanmaz `A` ve yerel adını `b`.</span><span class="sxs-lookup"><span data-stu-id="010ad-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="010ad-108">Bir öznitelik değeri ile neden olacağından `A:b`.</span><span class="sxs-lookup"><span data-stu-id="010ad-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="010ad-109">DOM Düzey 2 çağrısı ad alanı kullanan bir ortamda `setAttribute("A:b", "123")` önekine sahip bir öznitelik sonuçlanıyor `A` ve yerel adını `b`.</span><span class="sxs-lookup"><span data-stu-id="010ad-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="010ad-110">Microsoft .NET Framework DOM nasıl çalıştığını budur.</span><span class="sxs-lookup"><span data-stu-id="010ad-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="010ad-111">Bu nedenle, adı bir parametre alan tüm yöntemleri için bu yöntemleri adı nitelemek için bir önek de olur.</span><span class="sxs-lookup"><span data-stu-id="010ad-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="010ad-112">Name parametresi gibi `A:b` içinde **setAttribute** DOM düzey 1 yöntemi, aşağıdaki gibi Ayrıştırılan:</span><span class="sxs-lookup"><span data-stu-id="010ad-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
-   <span data-ttu-id="010ad-113">Hayır iki nokta üst üste (:) karakterler sonra yerel ad kümesine `name` parametresi, önek ve namespaceURI boş dizeler taşımaktadır.</span><span class="sxs-lookup"><span data-stu-id="010ad-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
-   <span data-ttu-id="010ad-114">İki nokta bulunursa, adı ilk iki nokta karakteri konumuna bağlı iki parçalara bölünür.</span><span class="sxs-lookup"><span data-stu-id="010ad-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="010ad-115">Önek dizesi iki nokta üst üste önce bulunamadı ayarlanır ve yerel ad sonra iki nokta üst üste bulunan dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="010ad-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="010ad-116">NamespaceURI değeri namespaceURI ediyorsa ve kalır almayan yöntemleri için boş dize olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="010ad-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="010ad-117">Aksi takdirde namespaceURI yönteme geçirilen dize ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="010ad-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="010ad-118">Önek tanımsızsa sonra **kaydetmek** yöntemi ve **InnerXml** ve **OuterXml** özellikleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="010ad-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010ad-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="010ad-119">See Also</span></span>  
 [<span data-ttu-id="010ad-120">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="010ad-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
