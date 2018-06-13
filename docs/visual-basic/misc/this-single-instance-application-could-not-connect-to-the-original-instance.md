---
title: Bu tek örnekli uygulama özgün örneğe bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 9bc1f33231cc4f29fabd100a695843beb334aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640260"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Bu tek örnekli uygulama özgün örneğe bağlanamadı
Bu tek örnekli uygulama özgün örneğine bağlanamadı. Bu sorunun olası nedeni bazıları şunlardır:  
  
-   Orijinal örnek yanıt vermeyi durdurdu.  
  
-   Uygulama çekirdek nesneleri oluşturma izni yok. Çekirdek nesneleri hakkında daha fazla bilgi için bkz: [zaman uyumu sağlayıcılar](../../standard/threading/mutexes.md).  
  
     Derleme GUID, ana sürüm numarası ve ikincil sürüm numarası birleştirme çekirdek nesneleri için temel adı gelir. Örneğin, bir taban adına olabilir `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Uygulama geliştirirken, bu hatayı düzeltmek için  
  
1.  Uygulama yanıt vermeyen bir duruma geçmez denetleyin.  
  
2.  Uygulama çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
3.  Özgün uygulama örneğini yeniden başlatın.  
  
4.  Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.  
  
5.  Hata oluştuğu durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri telefon.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı temel bilgileri](/visualstudio/debugger/debugger-basics)  

