---
title: 'Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 2934ff07026d520f52309e50eb7da24731608292
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786597"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)
Programınız tarafından başvurulan derlemeler otomatik olarak derleme zamanında yüklenir, ancak geçerli uygulama etki alanına çalışma zamanında belirli derlemeleri yüklemek mümkündür. Daha fazla bilgi için [nasıl yapılır: bir uygulama etki alanına derlemeleri](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Tüm içerdiği uygulama etki alanlarının kaldırmadan tek bir derlemeyi kaldırmak için hiçbir yolu yoktur. Derleme kapsamı dışında kalsa bile içerdiği tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklü kalır.  
  
 Bazı derlemeler, ancak diğerlerini kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturma, bu etki alanı içinde kod yürütme ve ardından, uygulama etki alanı kaldırılırken göz önünde bulundurun. Daha fazla bilgi için [nasıl yapılır: bir uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Uygulama etki alanına bir derlemeyi yüklemek için  
  
1.  Bazı yük sınıflarda yer yöntemleri kullanmak <xref:System.AppDomain> ve <xref:System.Reflection>. Daha fazla bilgi için [nasıl yapılır: bir uygulama etki alanına derlemeleri](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Uygulama etki alanını kaldırmak için  
  
1.  Tüm içerdiği uygulama etki alanlarının kaldırmadan tek bir derlemeyi kaldırmak için hiçbir yolu yoktur. Kullanım `Unload` yönteminden <xref:System.AppDomain> uygulama etki alanları kaldırmak için. Daha fazla bilgi için [nasıl yapılır: bir uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
- [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [Nasıl yapılır: Uygulama Etki Alanına Bütünleştirilmiş Kodlar Yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
