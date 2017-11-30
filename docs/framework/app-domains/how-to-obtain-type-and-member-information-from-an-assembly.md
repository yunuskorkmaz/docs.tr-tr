---
title: "Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9542fc8db84832437fb0d3b8e517ad4c7e01ca0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="9a78e-102">Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="9a78e-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="9a78e-103"><xref:System.Reflection> Ad alanı, bir derlemeye ait bilgileri almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="9a78e-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="9a78e-104">Bu bölüm aşağıdaki yöntemlerden birini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a78e-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="9a78e-105">Ek bilgi için bkz: [yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="9a78e-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="9a78e-106">Aşağıdaki örnek, bir derlemeden tür ve üye bilgilerini elde eder.</span><span class="sxs-lookup"><span data-stu-id="9a78e-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a78e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a78e-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="9a78e-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a78e-108">See Also</span></span>  
 [<span data-ttu-id="9a78e-109">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="9a78e-109">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="9a78e-110">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9a78e-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="9a78e-111">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="9a78e-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
