---
title: 'Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 390afb392c06d5ce003d69f028cd667deb4d86c8
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="dcf96-102">Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="dcf96-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="dcf96-103"><xref:System.Reflection> Ad alanı, bir derlemeye ait bilgileri almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="dcf96-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="dcf96-104">Bu bölüm aşağıdaki yöntemlerden birini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcf96-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="dcf96-105">Ek bilgi için bkz: [yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="dcf96-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="dcf96-106">Aşağıdaki örnek, bir derlemeden tür ve üye bilgilerini elde eder.</span><span class="sxs-lookup"><span data-stu-id="dcf96-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcf96-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcf96-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="dcf96-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dcf96-108">See Also</span></span>  
 <span data-ttu-id="dcf96-109">[Programlama uygulama etki alanları ile](./application-domains.md#programming-with-application-domains) [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)</span><span class="sxs-lookup"><span data-stu-id="dcf96-109">[Programming with Application Domains](./application-domains.md#programming-with-application-domains) [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md)</span></span>  
 [<span data-ttu-id="dcf96-110">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="dcf96-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
