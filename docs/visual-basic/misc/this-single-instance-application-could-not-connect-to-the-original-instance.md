---
title: "Bu tek örnekli uygulama özgün örneğe bağlanamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cb8cef696ba93f922dfe0d92195a5fb5147b4cc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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

