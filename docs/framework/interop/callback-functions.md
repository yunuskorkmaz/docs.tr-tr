---
title: Geri Çağırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66df62262d40b4102b9dbd55969e67b6e8041480
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703074"
---
# <a name="callback-functions"></a>Geri Çağırma İşlevleri
Kod, bir görevi tamamlamak, yönetilmeyen bir DLL işlevini yardımcı olan yönetilen bir uygulama içinde bir geri çağırma işlevidir. Bir geri arama işlev çağrıları, dolaylı olarak bir DLL işlevini aracılığıyla yönetilen bir uygulama geçirmek ve yönetilen bir uygulamasını yedekleyin. Bazı platformuyla adlı birçok DLL işlevleri çağırma düzgün çalışması için yönetilen kodda bir geri çağırma işlevini gerektirir.  
  
 Yönetilen koddan çoğu DLL işlevleri çağırmak için yönetilen bir işlevin tanımı oluşturun ve ardından çağırın. İşlem oldukça basittir.  
  
 Bir geri çağırma işlevini gerektiren bir DLL işlevini kullanarak bazı ek adımlar vardır. İlk olarak, işlevine yönelik belgelere bakarak işlevi bir geri çağırma gerekip gerekmediğini belirlemeniz gerekir. Sonra geri çağırma işlevi, yönetilen bir uygulamada oluşturmanız gerekir. Son olarak, bir işaretçi geri çağırma işlevine bağımsız değişken olarak geçirerek DLL işlevini çağırın. Aşağıdaki çizim, bu adımları özetler.  
  
 ![Platform çağırma geri çağırma](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")  
Geri arama işlevi ve uygulama  
  
 Geri çağırma işlevleri, bir görev art arda gerçekleştirilen durumlarda kullanım için idealdir. Başka bir ortak kullanımı numaralandırma işlevleri ile olduğu gibi **EnumFontFamilies**, **EnumPrinters**, ve **EnumWindows** Win32 API. **EnumWindows** aracılığıyla her penceresinde bir görevi gerçekleştirmek için geri çağrı işlevini çağırıp bilgisayarınızdaki tüm var olan windows işlev numaralandırır. Yönergeler ve örnek için bkz. [nasıl yapılır: Geri çağırma işlevlerini uygulama](../../../docs/framework/interop/how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Geri çağırma işlevlerini uygulama](../../../docs/framework/interop/how-to-implement-callback-functions.md)
- [DLL İşlevini Çağırma](../../../docs/framework/interop/calling-a-dll-function.md)
