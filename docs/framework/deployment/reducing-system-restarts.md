---
title: .NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e54dcb585c06f2bf49c41f763e03e5624a033442
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388914"
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
 [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
