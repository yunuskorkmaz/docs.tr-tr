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
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma
<xref:System.Reflection> Ad alanı, bir derlemeden bilgi almak için birçok yöntem içerir. Bu bölüm, aşağıdaki yöntemlerden birini gösterir. Ek bilgi için bkz: [yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md).  
  
 Aşağıdaki örnek, bir derlemeden tür ve üye bilgilerini alır.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama etki alanlarıyla programlama](./application-domains.md#programming-with-application-domains)
- [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
