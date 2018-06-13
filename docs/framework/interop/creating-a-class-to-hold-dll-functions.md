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
ms.openlocfilehash: 09088d1ac0a8312ee5832a5f3bc0547e6654de93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387068"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>DLL İşlevleri için bir Sınıf Oluşturma
Sık kullanılan DLL işlevini yönetilen sınıfında kaydırma platform işlevleri kapsülleyen etkili bir yaklaşımdır. Her durumda bunun için zorunlu olmasa da bir sınıf sarmalayıcı DLL işlevlerini tanımlama uygun olduğundan sağlama zahmetli ve hatalara eğilimli olabilir. Visual Basic veya C# programlama yapıyorsanız sınıfta veya Visual Basic modülü DLL işlevleri bildirmeniz gerekir.  
  
 Bir sınıf içinde aramak istediğiniz her DLL işlevi için statik bir yöntemi tanımlayın. Tanımı karakter kümesini veya yöntem bağımsız değişkenleri geçirme kullanılan çağırma gibi ek bilgileri içerebilir; Bu bilgileri kaldırarak, varsayılan ayarları seçin. Bildirim seçenekleri ve varsayılan ayarlarına tam listesi için bkz: [yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Başka bir sınıf üzerinde statik yöntemlerini çağıran gibi Sarmalanan sonra sınıfında yöntemleri çağırabilir. Platform çağırma tanıtıcıları arka plandaki işlevi otomatik olarak verilmiş.  
  
 Platform için bir yönetilen sınıf tasarlama çağırdığınızda, sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun. Örneğin, şunları yapabilirsiniz:  
  
-   Varolan bir sınıfa içinde DLL işlevleri bildirme.  
  
-   Yalıtılmış ve kolay bulmak işlevleri tutma her DLL işlevi için tek bir sınıf oluşturun.  
  
-   Mantıksal gruplar oluşturmak ve ek yükü azaltmak için ilgili DLL işlevleri kümesi için bir sınıf oluşturun.  
  
 Sınıf ve yöntemlerinden yazarken Lütfen adı verebilirsiniz. Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen DLL İşlevlerini Kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [DLL'lerde İşlevleri Tanımlama](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
