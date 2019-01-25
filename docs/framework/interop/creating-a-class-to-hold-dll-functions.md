---
title: DLL İşlevleri için bir Sınıf Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5718c70597acc6919c697a9033e8593865e60a2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745044"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>DLL İşlevleri için bir Sınıf Oluşturma
Sık kullanılan bir DLL işlevinin yönetilen sınıfta sarmalama platform işlevi kapsülleyen etkili bir yaklaşımdır. Her durumda bunu yapmak için zorunlu olmasa da, sınıf sarmalayıcı DLL işlevlerini tanımlama kullanışlı çünkü sağlamak hantal ve hataya eğilimli olabilir. Visual Basic'te programlama yapıyorsanız veya C#, DLL işlevleri bir sınıf veya Visual Basic module'u içinde bildirmeniz gerekir.  
  
 Bir sınıf içinde aramak istediğiniz her DLL işlevi için statik bir yöntem tanımlayın. Tanımı karakter kümesi veya çağırma yöntemi bağımsız değişkenleri geçirme içinde kullanılan gibi ek bilgiler içerebilir. Bu bilgiler gt;(yok) varsayılan ayarları seçin. Bildirim seçenekleri ve varsayılan ayarlarının tam listesi için bkz: [yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Üzerinde başka bir sınıfın statik yöntemleri çağırmak olarak sarmalanmış sonra sınıf üzerinde yöntemleri çağırabilir. Platform çağırma tanıtıcıları işlevi otomatik olarak verilen temel.  
  
 Platform için yönetilen sınıf tasarlama çağırdığınızda, sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun. Örneğin, şunları yapabilirsiniz:  
  
-   Varolan bir sınıf içinde DLL işlevleri bildirme.  
  
-   Yalıtılmış ve kolay bulmak işlevleri tutmak, her bir DLL işlevi için ayrı bir sınıf oluşturun.  
  
-   Bir dizi mantıksal gruplandırmaları form ve ek yükü azaltmak için ilgili DLL işlevleri için bir sınıf oluşturun.  
  
 Lütfen sınıfı ve metotlarını şekilde adlandırabilirsiniz. Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen DLL İşlevlerini Kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [DLL'lerde İşlevleri Tanımlama](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
