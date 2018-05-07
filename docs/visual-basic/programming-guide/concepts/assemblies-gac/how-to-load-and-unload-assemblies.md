---
title: 'Nasıl yapılır: yükleme ve kaldırma derlemeler (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 1cec7a7e15843874b65cf5d2f3a23b8e644a26d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Nasıl yapılır: yükleme ve kaldırma derlemeler (Visual Basic)
Programınız tarafından başvurulan derlemelerin otomatik olarak derleme zamanında yüklenir, ancak çalışma zamanında geçerli uygulama etki alanına belirli derlemeleri yüklemeye mümkündür. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur. Derleme kapsamı dışında kalsa bile içerdiği tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklü kalır.  
  
 Bazı derlemeleri ancak diğer kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturma, o etki alanı içinde kod yürütme ve o uygulama etki alanı yüklemeyi kaldırma göz önünde bulundurun. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Uygulama etki alanına bir derlemeyi yüklemek için  
  
1.  Bazı yük sınıflarda bulunan yöntemleri kullanma <xref:System.AppDomain> ve <xref:System.Reflection>. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Uygulama etki alanını kaldırmak için  
  
1.  Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur. Kullanım `Unload` yönteminden <xref:System.AppDomain> uygulama etki alanları kaldırmak için. Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Nasıl yapılır: Uygulama Etki Alanına Bütünleştirilmiş Kodlar Yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
