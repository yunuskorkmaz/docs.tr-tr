---
title: "Windows Formları Tasarımcısında Tasarım Zamanı Hataları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bb4899cbfaa5e378d58ec42c2bc8b39693c5f35
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Windows Formları Tasarımcısında Tasarım Zamanı Hataları
Bu konuda, Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesi kullanımını ve anlamı açıklanmaktadır. Bu hata listesi görünüyorsa, bunu Tasarımcısı'nda bir hata, ancak kodunuzdaki hataları düzeltmek için yardımcı yorumlar değil.  
  
 Bu hata listesi temel bir anlayış hatalarla ilgili ayrıntılı bilgileri sağlayarak ve olası çözümlerini öneren uygulamalarınızda hata ayıklamak yardımcı olur.  
  
## <a name="the-design-time-error-list-interface"></a>Tasarım zamanı hata listesi arabirimi  
 Windows Form Tasarımcısı yüklenmemesi durumunda bir hata listesi Tasarımcısı'nda görünür. Hataları kategorilerde gruplanır. Örneğin, bunlar bildirilmemiş değişkenin dört örneğini varsa, aynı hata kategoriye gruplandırılır. Her hata kategorisi hata özetler kısa bir açıklama içerir.  
  
 Genişletin veya bir hata kategorisi hata kategori başlığını tıklatarak veya Genişlet/Daralt Köşeli Çift Ayraca tıklayarak daraltın. Bir hata kategorisi genişlettiğinizde, aşağıdaki ek Yardım görüntülenir:  
  
-   Bu hata örnekleri.  
  
-   Bu hata ile yardımcı olur.  
  
-   Forum, bu hata hakkındaki gönderir.  
  
### <a name="instances-of-this-error"></a>Bu hata örnekleri  
 Ek hata geçerli projenizdeki tüm örneklerini listelemek Yardım. Birçok hata şu biçimde kesin bir konuma içerir: *[Proje adı]* *[Form adı]* satır:*[satır numarası]* sütun:*[sütun numarası]*. **Koda gitme olanağı** bağlantı kodunuzu hatanın oluştuğu konum alır.  
  
 Çağrı yığını şu hata ile ilişkili ise, tıklayabilirsiniz **çağrı yığını Göster** bağlantı, çağrı yığını göstermek için hata, daha fazla genişletir. Yığın inceleyerek hata ayıklama değerli bilgiler sağlayabilir. Örneğin, bir hata oluştu önce adı veriliyordu işlevleri izleyebilirsiniz. Çağrı yığını seçilebilir, böylelikle kopyalayın ve kaydedin.  
  
> [!NOTE]
>  Visual Basic'te tasarım zamanı hata listesi birden fazla hata görüntülemez ancak birden çok örneğini aynı hatayı gösteriyor olabilir. Visual C++'da, hataları bağlantılar/satır numarası bağlantılar goto kodu yok.  
  
### <a name="help-with-this-error"></a>Bu hata ile Yardım  
 Hata bir ilişkili MSDN Yardım konusunun bağlantısını içeriyorsa, Ek Yardım Yardım konusunun bağlantısını içerir. Bağlantıya tıkladığında, ilişkili Yardım konusu Visual Studio'da görüntülenir.  
  
### <a name="forum-posts-about-this-error"></a>Bu hata hakkındaki Forumu gönderir  
 Ek Yardım hata ile ilgili MSDN Forumu gönderileri bağlantısını içerir. Forum, hata iletisi dizesi göre aranır. Ayrıca, aşağıdaki forumları arama deneyebilirsiniz:  
  
-   [Windows Forms Tasarımcısı Forumu](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms forumları](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Yoksay ve devam et  
 Hata koşulu yoksayıp Tasarımcı yüklemeye devam etmek seçebilirsiniz. Bu eylem seçme beklenmeyen davranışlara neden olabilir. Örneğin, denetimleri tasarım yüzeyine görünmeyebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım zamanı geliştirme sorunlarını giderme](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Denetim ve Bileşen Yazmada Sorun Giderme](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Windows Form Tasarımcısı hata iletileri](http://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
