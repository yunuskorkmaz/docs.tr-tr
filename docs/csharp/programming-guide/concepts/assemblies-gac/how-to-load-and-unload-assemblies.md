---
title: 'Nasıl yapılır: Derlemeleri (C#) yükle ve Kaldır'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 3f3c244a74e029eeaead77f561cd4c1adfca519a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595842"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Nasıl yapılır: Derlemeleri (C#) yükle ve Kaldır
Programınızın başvurduğu derlemeler derleme zamanında otomatik olarak yüklenir, ancak çalışma zamanında geçerli uygulama etki alanına belirli derlemeler yüklemek de mümkündür. Daha fazla bilgi için [nasıl yapılır: Derlemeleri bir uygulama etki alanına](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)yükleyin.  
  
 Tek bir derlemeyi, kendisini içeren tüm uygulama etki alanlarının kaldırılmasına gerek kalmadan kaldırma yöntemi yoktur. Derleme kapsam dışına çıksa bile, kendisini içeren tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklenmeyecektir.  
  
 Bazı derlemeleri kaldırmak istiyorsanız, ancak diğerlerini değil, yeni bir uygulama etki alanı oluşturmayı, bu etki alanı içinde kodu yürütmeyi ve ardından bu uygulama etki alanını kaldırmayı düşünün. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanını](../../../../framework/app-domains/how-to-unload-an-application-domain.md)kaldırın.  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Bir derlemeyi uygulama etki alanına yüklemek için  
  
1. <xref:System.AppDomain> Sınıflarda<xref:System.Reflection>bulunan çeşitli yükleme yöntemlerinden birini kullanın. Daha fazla bilgi için [nasıl yapılır: Derlemeleri bir uygulama etki alanına](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)yükleyin.  
  
### <a name="to-unload-an-application-domain"></a>Bir uygulama etki alanını kaldırmak için  
  
1. Tek bir derlemeyi, kendisini içeren tüm uygulama etki alanlarının kaldırılmasına gerek kalmadan kaldırma yöntemi yoktur. Uygulama etki alanlarını kaldırmak <xref:System.AppDomain> için ' den metodunukullanın.`Unload` Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanını](../../../../framework/app-domains/how-to-unload-an-application-domain.md)kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../index.md)
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
- [Nasıl yapılır: Derlemeleri bir uygulama etki alanına yükleme](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
