---
title: Geri Çağırma İşlevleri
description: Yönetilmeyen DLL işlevinin bir görevi tamamlarına yardımcı olan, yönetilen bir uygulamayla kod olan geri çağırma işlevleri hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 659f384f7bfc3a2326a40a9536c977d7c41ab076
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283165"
---
# <a name="callback-functions"></a>Geri Çağırma İşlevleri

Bir geri çağırma işlevi, yönetilmeyen bir DLL işlevinin bir görevi tamammesine yardımcı olan bir yönetilen uygulama içindeki koddur. Bir geri çağırma işlevine yapılan çağrılar, yönetilen bir uygulamadan, bir DLL işlevi aracılığıyla ve yönetilen uygulamaya geri dönerek dolaylı olarak geçer. Platform çağırma ile çağrılan birçok DLL işlevinden bazıları, yönetilen kodda düzgün şekilde çalışması için bir geri çağırma işlevi gerektirir.  
  
 Yönetilen koddan çoğu DLL işlevini çağırmak için, işlevin yönetilen bir tanımını oluşturun ve ardından bunu çağırın. İşlem basittir.  
  
 Bir geri çağırma işlevi gerektiren DLL işlevinin kullanılması bazı ek adımlara sahiptir. Önce, işlevin belgelerine bakarak işlevin geri çağırma gerektirip gerektirmediğini belirlemelisiniz. Ardından, yönetilen uygulamanızda geri çağırma işlevini oluşturmanız gerekir. Son olarak, DLL işlevini çağırır ve geri çağırma işlevine bir işaretçiyi bir bağımsız değişken olarak geçirerek.

 Aşağıdaki çizim, geri çağırma işlevini ve uygulama adımlarını özetler:  
  
 ![Platform çağırma geri çağırma işlemini gösteren diyagram.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Geri çağırma işlevleri, bir görevin tekrar tekrar gerçekleştirildiği durumlarda kullanım için idealdir. Diğer bir yaygın kullanım, Windows API 'sindeki **Enumfontaileleri**, **EnumPrinters** ve **EnumWindows** gibi numaralandırma işlevleridir. **EnumWindows** işlevi, her pencerede bir görevi gerçekleştirmek için geri çağırma işlevini çağırarak bilgisayarınızdaki mevcut tüm pencereleri sıralar. Yönergeler ve bir örnek için bkz. [nasıl yapılır: geri çağırma Işlevlerini uygulama](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama](how-to-implement-callback-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
