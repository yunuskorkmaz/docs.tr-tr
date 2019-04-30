---
title: 'Nasıl yapılır: Uygulama Etki Alanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff85f5737babb73d87f4918ca0f4981263f7dadc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705720"
---
# <a name="how-to-create-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanı Oluşturma
Gerektiğinde, bir ortak dil çalışma zamanı ana uygulama etki alanları otomatik olarak oluşturur. Ancak, kendi uygulama etki alanları oluşturmak ve bunlara kişisel yönetmek istediğiniz bu derlemeleri yükleyin. Ayrıca, kod yürütme uygulama etki alanları oluşturabilirsiniz.  
  
 Aşırı yüklenen birini kullanarak yeni bir uygulama etki alanı oluşturma **CreateDomain** yöntemleri <xref:System.AppDomain?displayProperty=nameWithType> sınıfı. Uygulama etki alanına bir ad verin ve bu adla başvurun.  
  
 Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, ad atar `MyDomain`ve ardından adını ana etki alanı ve yeni oluşturulan alt uygulama etki alanı konsola yazdırır.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
