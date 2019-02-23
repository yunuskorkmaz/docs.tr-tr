---
title: 'Nasıl yapılır: Yük derlemeleri ve yüklemelerini kaldırma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 77dc773c9e32c293ab5155b15e45f5255e31ab9a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745217"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Nasıl yapılır: Yük derlemeleri ve yüklemelerini kaldırma (Visual Basic)
Programınız tarafından başvurulan derlemeler otomatik olarak derleme zamanında yüklenir, ancak geçerli uygulama etki alanına çalışma zamanında belirli derlemeleri yüklemek mümkündür. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanına derlemeler yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Tüm içerdiği uygulama etki alanlarının kaldırmadan tek bir derlemeyi kaldırmak için hiçbir yolu yoktur. Derleme kapsamı dışında kalsa bile içerdiği tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklü kalır.  
  
 Bazı derlemeler, ancak diğerlerini kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturma, bu etki alanı içinde kod yürütme ve ardından, uygulama etki alanı kaldırılırken göz önünde bulundurun. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Uygulama etki alanına bir derlemeyi yüklemek için  
  
1.  Bazı yük sınıflarda yer yöntemleri kullanmak <xref:System.AppDomain> ve <xref:System.Reflection>. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanına derlemeler yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Uygulama etki alanını kaldırmak için  
  
1.  Tüm içerdiği uygulama etki alanlarının kaldırmadan tek bir derlemeyi kaldırmak için hiçbir yolu yoktur. Kullanım `Unload` yönteminden <xref:System.AppDomain> uygulama etki alanları kaldırmak için. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
- [.NET derlemeleri](../../../../standard/assembly/index.md)
- [Nasıl yapılır: Uygulama etki alanına derlemeler yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
