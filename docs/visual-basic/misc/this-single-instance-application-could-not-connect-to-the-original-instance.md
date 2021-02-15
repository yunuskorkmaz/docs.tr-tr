---
description: 'Hakkında daha fazla bilgi edinin: Bu tek örnekli uygulama özgün örneğe bağlanamadı'
title: Bu tek örnekli uygulama özgün örneğe bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 123cf2cded43c10d0f538fc12f31f4065caeb6dd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427939"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Bu tek örnekli uygulama özgün örneğe bağlanamadı

Bu tek örnekli uygulama özgün örneğe bağlanamadı. Bu sorunun olası nedenlerinden bazıları şunlardır:  
  
- Özgün örnek yanıt vermeyi durdurdu.  
  
- Uygulamanın çekirdek nesneleri oluşturma izni yok. Çekirdek nesneler hakkında daha fazla bilgi için bkz. zaman [uyumu sağlayıcılar](../../standard/threading/mutexes.md).  
  
     Çekirdek nesnelerinin temel adı, derlemenin GUID, ana sürüm numarası ve alt sürüm numarasını birleştirerek alınır. Örneğin, taban adı olabilir `3639f15d-9547-43da-8145-60da347829915.1` .  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Uygulamayı geliştirirken bu hatayı düzeltmek için  
  
1. Uygulamanın yanıt vermeyen bir duruma gitmediğinden emin olun.  
  
2. Uygulamanın çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
3. Uygulamanın orijinal örneğini yeniden başlatın.  
  
4. Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanan herhangi bir işlemi temizlemek için bilgisayarı yeniden başlatın.  
  
5. Hatanın oluştuğu koşulları ve telefon Microsoft Ürün Destek Hizmetleri ' ni aklınızda yapın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Temel Bilgileri](/visualstudio/debugger/debugger-feature-tour)
