---
title: "Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)
Programınız tarafından başvurulan derlemelerin otomatik olarak derleme zamanında yüklenir, ancak çalışma zamanında geçerli uygulama etki alanına belirli derlemeleri yüklemeye mümkündür. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur. Derleme kapsamı dışında kalsa bile içerdiği tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklü kalır.  
  
 Bazı derlemeleri ancak diğer kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturma, o etki alanı içinde kod yürütme ve o uygulama etki alanı yüklemeyi kaldırma göz önünde bulundurun. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Uygulama etki alanına bir derlemeyi yüklemek için  
  
1.  Bazı yük sınıflarda bulunan yöntemleri kullanma <xref:System.AppDomain> ve <xref:System.Reflection>. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Uygulama etki alanını kaldırmak için  
  
1.  Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur. Kullanım `Unload` yönteminden <xref:System.AppDomain> uygulama etki alanları kaldırmak için. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Nasıl yapılır: uygulama etki alanına derlemeler yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
