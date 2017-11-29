---
title: ".NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0019931c0ebe2bfef7ce8db72b768f31ad67f938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yükleyici kullanan [yeniden başlatma Yöneticisi](http://go.microsoft.com/fwlink/?LinkId=231425) sistem önlemek için mümkün olduğunca yükleme sırasında yeniden başlatır. Uygulama kurulum programı .NET Framework yüklerse, yeniden başlatma bu özelliğin avantajlarından yararlanmak için Yöneticisi ile arabirim oluşturabilirler. Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework 4.5 yükleyici ilerlemesini almak](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Nedenlerden dolayı yeniden başlatma  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yükleme .NET Framework 4 uygulama yükleme sırasında kullanılmıyorsa, sistemin yeniden başlatılmasını gerektirir. Bunun nedeni, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] .NET Framework 4 dosyalarının yerini alır ve bu dosyalar yükleme sırasında kullanılabilir olmasını gerektirir. Çoğu durumda, kullanımda olmayan erken önlem algılama ve closing.NET Framework 4 uygulamalar tarafından yeniden başlatılması engellenebilir. Ancak, bazı sistem uygulamalar kapatılmalıdır değil. Bu durumda, yeniden başlatma kaçınılmaz.  
  
## <a name="end-user-experience"></a>Son kullanıcı deneyimi  
 Tam yüklemesi yapan bir son kullanıcı, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yükleyici .NET Framework 4 uygulamaları kullanımda algılarsa, sistemin yeniden başlatılmasını önlemek için Fırsat verilir. Bir ileti tüm çalışan .NET Framework 4 uygulamaları listeler ve yüklemeden önce bu uygulamaları kapatın seçeneği sunar. Kullanıcı onaylarsa, bu uygulamalar yükleyici tarafından kapatılır ve bir sistem yeniden başlatma önlenmiş olur. Kullanıcının belirli bir miktar süre içinde iletisine yanıt vermiyorsa uygulamalardan kapatmadan yükleme devam eder.  
  
 Yeniden başlatma Yöneticisi sistem yeniden başlatılması çalışan uygulamalar olsa bile bir durum kapalı algılarsa, ileti görüntülenmez.  
  
 ![Uygulama iletişim kapatmak](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
Kullanımda olan .NET Framework uygulamaları kapatma istemi  
  
## <a name="using-a-chained-installer"></a>Zincirleme Yükleyicisi'ni kullanarak  
 .NET Framework ile uygulamanızı yeniden dağıtmak istediğiniz, ancak kendi kurulum programı ve kullanıcı Arabirimi kullanmak istediğiniz (zincir) .NET Framework Kurulum işlemi, Kurulum işlemi ekleyebilirsiniz. Zincirleme yüklemeler hakkında daha fazla bilgi için bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md). Zincirleme içinde sistem yeniden başlatmalarını azaltmak için .NET Framework yükleyici, Kurulum programı kapatmak için uygulamalar listesini sağlar. Kurulum programı kullanıcının bir ileti kutusu gibi bir kullanıcı arabirimi üzerinden bu bilgileri sağlayın gerekir, kullanıcının yanıtını alma ve yanıtı .NET Framework yükleyici geçirin. Zincirleme yükleyici örneği için bkz: [nasıl yapılır: .NET Framework 4.5 yükleyici ilerlemesini almak](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Zincirleme yükleyici kullanmakta olduğunuz ancak uygulamaları kapatma için kendi ileti kutusu sağlamak ister misiniz, kullanabileceğiniz `/showrmui` ve `/passive` .NET Framework zincir oluşturduğunuzda komut satırında seçenekleri Kurulum işlemi. Bu seçenekler birlikte kullanıldığında, yükleyici sistemin yeniden başlatılmasını önlemek için kapatılabilir, uygulamaları kapatmak için ileti kutusu gösterir. Tam kullanıcı arabirimi altında yaptığı gibi bu ileti kutusu edilgen modda aynı şekilde davranır. Bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md) tamamını .NET Framework yeniden dağıtılabilir için komut satırı seçenekleri için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dağıtım](../../../docs/framework/deployment/index.md)  
 [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu alma](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
