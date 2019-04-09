---
title: 'Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma'
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
ms.openlocfilehash: 9f9d01715a9635b276ca87d94082bb4d3820084e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138885"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="e1431-102">Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="e1431-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="e1431-103"><xref:System.Reflection> Ad alanı, bir derlemeden bilgi almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="e1431-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="e1431-104">Bu bölüm, aşağıdaki yöntemlerden birini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1431-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="e1431-105">Ek bilgi için bkz: [yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="e1431-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="e1431-106">Aşağıdaki örnek, bir derlemeden tür ve üye bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e1431-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1431-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1431-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="e1431-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1431-108">See also</span></span>

- [<span data-ttu-id="e1431-109">Uygulama Etki Alanlarıyla Programlama</span><span class="sxs-lookup"><span data-stu-id="e1431-109">Programming with Application Domains</span></span>](./application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="e1431-110">Yansıma</span><span class="sxs-lookup"><span data-stu-id="e1431-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="e1431-111">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e1431-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
