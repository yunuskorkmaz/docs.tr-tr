---
title: 'Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: fe9f78e145e6b7bc8ef138ff5cdb98aa345b90c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Nasıl yapılır: Uygulama Etki Alanına Bütünleştirilmiş Kodlar Yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
