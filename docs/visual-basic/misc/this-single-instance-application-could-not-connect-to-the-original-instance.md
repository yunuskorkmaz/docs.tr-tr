---
title: Bu tek örnekli uygulama özgün örneğe bağlanamadı
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198132"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Bu tek örnekli uygulama özgün örneğe bağlanamadı
Bu tek örnekli uygulama özgün örneğe bağlanamadı. Bu sorunun olası nedenlerinden bazıları şunlardır:  
  
- Özgün örnek yanıt vermeyi durdurdu.  
  
- Uygulamanın çekirdek nesneleri oluşturma izni yok. Çekirdek nesneler hakkında daha fazla bilgi için bkz. zaman [uyumu sağlayıcılar](../../standard/threading/mutexes.md).  
  
     Çekirdek nesnelerinin temel adı, derlemenin GUID, ana sürüm numarası ve alt sürüm numarasını birleştirerek alınır. Örneğin, temel ad `3639f15d-9547-43da-8145-60da347829915.1`olabilir.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Uygulamayı geliştirirken bu hatayı düzeltmek için  
  
1. Uygulamanın yanıt vermeyen bir duruma gitmediğinden emin olun.  
  
2. Uygulamanın çekirdek nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.  
  
3. Uygulamanın orijinal örneğini yeniden başlatın.  
  
4. Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanan herhangi bir işlemi temizlemek için bilgisayarı yeniden başlatın.  
  
5. Hatanın oluştuğu koşulları ve telefon Microsoft Ürün Destek Hizmetleri ' ni aklınızda yapın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı Temel Bilgileri](/visualstudio/debugger/debugger-feature-tour)
