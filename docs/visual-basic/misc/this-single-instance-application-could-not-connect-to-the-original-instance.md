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
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [NIB: Nasıl yapılır: bir uygulama (Visual Basic) davranışı depolamasına belirtin](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [Hata ayıklayıcı temel bilgileri](/visualstudio/debugger/debugger-basics)  
 [PAVEOVER ürün desteği ve erişilebilirlik](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
