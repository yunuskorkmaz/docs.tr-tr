---
title: "Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed9669479a3854c843716a1aeb37f7701ea7d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Nasıl yapılır: WPF Uygulamasına Giriş Ekranı Ekleme
Bu konuda bir başlangıç penceresi eklemeyi gösterir veya *ekranı*, bir Windows Presentation Foundation (WPF) uygulaması için.  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a>Varolan bir görüntü giriş ekranı eklemek için  
  
1.  Oluşturun veya ekranı için kullanmak istediğiniz görüntü bulun. Windows görüntüleme bileşeni (WIC) tarafından desteklenen herhangi bir resim biçimi kullanabilirsiniz. Örneğin, BMP, GIF, JPEG, PNG veya TIFF biçimini kullanabilirsiniz.  
  
2.  Görüntü dosyası WPF uygulaması projesine ekleyin. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
3.  Çözüm Gezgini'nde, görüntüyü seçin.  
  
4.  Aşağı açılan okunu Özellikler penceresinde **yapı eylemi** özelliği.  
  
5.  Seçin **KarşılamaEkranı** aşağı açılan listeden.  
  
    > [!NOTE]
    >  Görmüyorsanız, **KarşılamaEkranı** seçeneği, kullanmakta olduğunuz kontrol ettiğinizden emin olun [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 veya sonraki bir sürümü.  
  
6.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Giriş ekranı görüntüsü ekran ortasında görünür ve ana uygulama penceresi göründüğünde kaybolur.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Giriş ekranı uygulamayı kaldırmak için  
  
1.  Çözüm Gezgini'nde giriş ekranı görüntüsü seçin.  
  
2.  Özellikler penceresinde ayarlayın **yapı eylemi** için **hiçbiri**.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Giriş ekranı uygulamayı kaldırmak için  
  
-   Çözüm Gezgini'nde giriş ekranı görüntüsü silin.  
  
-   Karşılama ekranı resmini projeden çıkarın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.SplashScreen>  
 [NIB: nasıl yapılır: Varolan öğeleri için bir proje ekleyin](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
