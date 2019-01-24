---
title: 'Nasıl yapılır: COM başvurusu .NET türlerinden'
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
ms.openlocfilehash: 9826f8af06693fdff0d5bea75cfa3f2586faa4f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582130"
---
# <a name="how-to-reference-net-types-from-com"></a>Nasıl yapılır: COM başvurusu .NET türlerinden
Bakış açısıyla, istemci ve sunucu kodu, COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez. Microsoft Visual Basic istemciler, bir .NET nesnesini sözdizimi, özelliklerini ve nesne yöntemleri ve tam olarak bunu herhangi bir COM nesnesi gibi alanlar nesne tarayıcısında görüntüleyebilirsiniz.  
  
 Meta veriler için bir COM tür kitaplığı dışarı aktarmak için aynı araçları kullanmanıza rağmen bir tür kitaplığını içeri aktarma işlemi C++ istemciler için biraz daha karmaşıktır. .NET nesne üyeleri bir yönetilmeyen C++ istemcisinden başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosyasına başvurmak **#import** yönergesi. Bir tür kitaplığı C++'tan başvururken ya da belirtmelisiniz **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımlarını içe aktarın.  
  
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
- [Bir .NET nesnesini çağırma](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))
- [COM erişimi için bir uygulama dağıtma](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
