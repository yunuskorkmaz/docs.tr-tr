---
title: Bu tek örnekli uygulama özgün örneğine bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 7ffa9b185e16cfdf8223ce84e77d1a0e1fa67f65
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322660"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Bu tek örnekli uygulama özgün örneğine bağlanamadı
Bu tek örnekli uygulama özgün örneğine bağlanamadı. Bu sorunun olası nedeni bazıları şunlardır:  
  
-   Özgün örneğe yanıt vermeyi durdurdu.  
  
-   Uygulama, çekirdek nesneleri oluşturma izni yok. Çekirdek nesneleri hakkında daha fazla bilgi için bkz. [mutex'ler](../../standard/threading/mutexes.md).  
  
     Derlemenin GUID, ana sürüm numarası ve küçük versiyon numarasını birleştirerek çekirdek nesneler için taban adı gelir. Örneğin, temel adı olabilir `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Uygulama geliştirirken, bu hatayı düzeltmek için  
  
1. Uygulama bir yanıt veremez duruma geçmez denetleyin.  
  
2. Uygulama çekirdek nesneleri oluşturmak için yeterli izinlere sahip olduğunu denetleyin.  
  
3. Özgün uygulama örneğini yeniden başlatın.  
  
4. Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.  
  
5. Altında hatanın gerçekleştiği durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri telefon.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Temel Bilgileri](/visualstudio/debugger/debugger-basics)
