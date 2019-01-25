---
title: 'Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef3fbb7af3097a67cb39f0c3b2ee294b86f0600e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701605"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="d9da5-102">Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="d9da5-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="d9da5-103"><xref:System.Reflection> Ad alanı, bir derlemeden bilgi almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="d9da5-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="d9da5-104">Bu bölüm, aşağıdaki yöntemlerden birini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9da5-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="d9da5-105">Ek bilgi için bkz: [yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="d9da5-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="d9da5-106">Aşağıdaki örnek, bir derlemeden tür ve üye bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d9da5-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9da5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9da5-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d9da5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9da5-108">See also</span></span>
- [<span data-ttu-id="d9da5-109">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="d9da5-109">Programming with Application Domains</span></span>](./application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="d9da5-110">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d9da5-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="d9da5-111">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="d9da5-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
