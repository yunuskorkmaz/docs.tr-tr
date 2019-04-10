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
ms.openlocfilehash: 9b7e8a4d92661b974fba7c88989891b30e54e94d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218458"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yükleyicisi [yeniden başlatma Yöneticisi](https://go.microsoft.com/fwlink/?LinkId=231425) sistem önlemek için mümkün olduğunca yükleme sırasında yeniden başlatır. Uygulama kurulum programınıza .NET Framework yüklerse, yeniden başlatma bu özellikten yararlanmak için Yöneticisi ile arabirim oluşturmasını. Daha fazla bilgi için [nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Yeniden başlatma nedeniyle  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yükleme yüklenmesi sırasında bir .NET Framework 4 uygulama seçeneği kullanılıyorsa sistemin yeniden başlatılmasını gerektirir. Bunun nedeni, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] .NET Framework 4 dosyalarının yerini alır ve bu dosyalar yükleme sırasında kullanılabilir olmasını gerektirir. Çoğu durumda, yeniden başlatma, kullanımda olan sıd'lerde algılama ve closing.NET Framework 4 uygulamaları tarafından engellenebilir. Ancak, bazı sistem uygulamalar kapatılmalıdır değil. Bu durumlarda, yeniden başlatma kaçınılmaz.  
  
## <a name="end-user-experience"></a>Son kullanıcı deneyimi  
 Tam yüklemesi yapan bir son kullanıcı, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yükleyici kullanımda .NET Framework 4 uygulamaları algılarsa sistemin yeniden başlatılmasını önlemek için fırsatı verilir. Bir ileti, tüm çalışan .NET Framework 4 uygulamalarını listeler ve yüklemeden önce bu uygulamaları kapatın seçeneği sunar. Kullanıcıyı onaylarsa, bu uygulamalar yükleyici tarafından kapatılır ve sistemin yeniden başlatılması önlenmiş olur. Kullanıcı iletiye bir belirli bir süre içinde yanıt vermezse, herhangi bir uygulamayı kapatmadan yüklemesi devam eder.  
  
 Yeniden başlatma Yöneticisi çalışan uygulamalar olsa bile bir sistem yeniden başlatma gerektiren bir durumu kapalı algılarsa, bu ileti görüntülenmez.  
  
 ![Uygulama iletişim kapatmak](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
Kullanımda olan .NET Framework uygulamaları kapatmak için istemi  
  
## <a name="using-a-chained-installer"></a>Zincirleme bir yükleyici kullanarak  
 Uygulamanızla birlikte .NET Framework yeniden dağıtmak istediğiniz, ancak kendi kurulum programı ve UI kullanmak istediğiniz, (bağlayabilirsiniz) .NET Framework Kurulum işlemi, Kurulum işlemine dahil edebilirsiniz. Zincirleme hakkında daha fazla bilgi için bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md). Zincirleme içinde sistem yeniden başlatmalarını azaltmak için Kurulum programınızı kapatmak için uygulamalar listesinde ile .NET Framework yükleyicisi sağlar. Kurulum programınıza gerekir, kullanıcıya bir ileti kutusu gibi bir kullanıcı arabirimi aracılığıyla bu bilgileri sağlayın, kullanıcının yanıt alın ve ardından yanıt .NET Framework yükleyicisi geçirin. Zincirleme bir yükleyici örneği için bkz [nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Zincirleme bir yükleyici kullanıyorsanız ancak uygulamaları kapatmak için kendi ileti kutusunu sağlamayı istemediğiniz, kullanabileceğiniz `/showrmui` ve `/passive` Kurulum Seçenekleri .NET Framework bağladığınızda komut satırında işlemi. Bu seçenekler birlikte kullandığınızda, yükleyici sistemin yeniden başlatılmasını önlemek için kapatılabilir, uygulamaları kapatmak için ileti kutusu gösterir. Tam kullanıcı arabiriminin çalıştığı gibi bu ileti kutusu pasif modda aynı şekilde davranır. Bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md) için .NET Framework yeniden dağıtılabilir için komut satırı seçeneklerinin tam bir set.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](../../../docs/framework/deployment/index.md)
- [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Nasıl yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
