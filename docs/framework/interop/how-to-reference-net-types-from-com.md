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
ms.openlocfilehash: 0223cb25b933cc84af49aa86d90259fdf1fd3efc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124168"
---
# <a name="how-to-reference-net-types-from-com"></a>Nasıl yapılır: COM'dan .NET Türlerine Başvurma
İstemci ve sunucu kodunun bakış noktasından, COM ile .NET Framework arasındaki farklar büyük ölçüde görünmez değildir. Microsoft Visual Basic istemcileri, nesne yöntemleri ve söz dizimi, Özellikler ve alanları tamamen başka bir COM nesnesi gibi sunan nesne tarayıcısında bir .NET nesnesini görüntüleyebilir.  
  
 Bir tür kitaplığını içeri aktarma işlemi, C++ istemcileri için biraz daha karmaşıktır, ancak meta verileri bir COM tür kitaplığına aktarmak için aynı araçları kullanabilirsiniz. Yönetilmeyen bir C++ istemcisinden .NET nesne üyelerine başvurmak için **#import** YÖNERGESI ile TLB dosyasına (Tlbexp. exe ile üretildi) başvurun. C++ ' dan bir tür kitaplığına başvurulduğunda, **raw_interfaces_only** seçeneğini belirtmeniz veya tanımları, mscorlib. tlb temel sınıf kitaplığında içeri aktarmanız gerekir.  
  
### <a name="to-import-a-library"></a>Bir kitaplığı içeri aktarmak için  
  
- **#İmport** yönergesinde **raw_interfaces_only** seçeneğini belirtin. Örneğin:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     -veya-  
  
- Mscorlib. tlb için bir #import yönergesi ekleyin. Örneğin:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Derlemeleri COM ile Kaydetme](registering-assemblies-with-com.md)
- [.NET nesnesi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [COM erişimi için uygulama dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
