---
title: Geri Çağırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181512"
---
# <a name="callback-functions"></a>Geri Çağırma İşlevleri
Geri arama işlevi, yönetilmeyen bir DLL işlevinin görevi tamamlamasına yardımcı olan yönetilen bir uygulama içindeki koddur. Geri arama işlevine yapılan çağrılar, yönetilen bir uygulamadan, Bir DLL işlevi aracılığıyla ve yönetilen uygulamaya dolaylı olarak geçer. Platform çağrıcağı ile çağrılan birçok DLL işlevinden bazıları, düzgün çalışması için yönetilen kodda bir geri arama işlevi gerektirir.  
  
 Yönetilen koddan çoğu DLL işlevini çağırmak için, işlevin yönetilen bir tanımını oluşturun ve sonra onu çağırırsınız. İşlem basittir.  
  
 Geri arama işlevi gerektiren bir DLL işlevinin kullanılmasının bazı ek adımları vardır. İlk olarak, işlev için belgelere bakarak işlevin bir geri arama gerektirip gerektirmediğini belirlemeniz gerekir. Ardından, yönetilen uygulamanızda geri arama işlevini oluşturmanız gerekir. Son olarak, dll işlevini çağırın, bir işaretçiyi bağımsız değişken olarak geri arama işlevine geçersiniz.

 Aşağıdaki resimde geri arama işlevi ve uygulama adımları özetlenebilir:  
  
 ![Platformu gösteren diyagram geri arama işlemini çağırır.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Geri arama işlevleri, görevin tekrar tekrar gerçekleştirildiği durumlarda kullanım için idealdir. Başka bir yaygın kullanım numaralandırma fonksiyonları ile, **EnumFontFamilies**gibi , **EnumPrinters** **,** windows API. **EnumWindows** işlevi bilgisayarınızdaki varolan tüm pencerelerden birime direnerek, her pencerede bir görevi gerçekleştirmek için geri arama işlevini çağırır. Yönergeler ve bir örnek için [bkz.](how-to-implement-callback-functions.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama](how-to-implement-callback-functions.md)
- [DLL İşlevini Çağırma](calling-a-dll-function.md)
