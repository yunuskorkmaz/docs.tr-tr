---
title: "Nasıl yapılır: COM'dan .NET Türlerine Başvurma"
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e033ba4b3b98367452b355363058adc7f1a5887
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198406"
---
# <a name="how-to-reference-net-types-from-com"></a>Nasıl yapılır: COM'dan .NET Türlerine Başvurma
Bakış açısıyla, istemci ve sunucu kodu, COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez. Microsoft Visual Basic istemciler, bir .NET nesnesini sözdizimi, özelliklerini ve nesne yöntemleri ve tam olarak bunu herhangi bir COM nesnesi gibi alanlar nesne tarayıcısında görüntüleyebilirsiniz.  
  
 Meta veriler için bir COM tür kitaplığı dışarı aktarmak için aynı araçları kullanmanıza rağmen bir tür kitaplığını içeri aktarma işlemi C++ istemciler için biraz daha karmaşıktır. .NET nesne üyeleri bir yönetilmeyen C++ istemcisinden başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosyasına başvurmak **#import** yönergesi. Tür kitaplığından başvururken C++, ya da belirtmeniz gerekir **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımlarını içe aktarın.  
  
### <a name="to-import-a-library"></a>Bir kitaplığı içeri aktarmak için  
  
-   Belirtin **raw_interfaces_only** seçeneğini **#import** yönergesi. Örneğin:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     -veya-  
  
-   #İmport yönergesi için Mscorlib.tlb içerir. Örneğin:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Bütünleştirilmiş Kodları COM ile Kaydetme](registering-assemblies-with-com.md)
- [Bir .NET nesnesini çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [COM erişimi için bir uygulama dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
