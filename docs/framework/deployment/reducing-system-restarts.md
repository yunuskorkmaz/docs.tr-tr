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
ms.openlocfilehash: a491b0efd38ed7ff37c8c704b6646dddede5efb3
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379914"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
.NET Framework 4.5 yükleyicisi [yeniden başlatma Yöneticisi](https://go.microsoft.com/fwlink/?LinkId=231425) sistem önlemek için mümkün olduğunca yükleme sırasında yeniden başlatır. Uygulama kurulum programınıza .NET Framework yüklerse, yeniden başlatma bu özellikten yararlanmak için Yöneticisi ile arabirim oluşturmasını. Daha fazla bilgi için [nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Yeniden başlatma nedeniyle  
 .NET Framework 4 uygulama yüklemesi sırasında kullanılmıyorsa, .NET Framework 4.5 sistemin yeniden başlatılmasını gerektirir. .NET Framework 4.5, .NET Framework 4 dosyalarının yerini alır ve bu dosyalar yükleme sırasında kullanılabilir olmasını gerektiren olmasıdır. Çoğu durumda, yeniden başlatma, kullanımda olan sıd'lerde algılama ve closing.NET Framework 4 uygulamaları tarafından engellenebilir. Ancak, bazı sistem uygulamalar kapatılmalıdır değil. Bu durumlarda, yeniden başlatma kaçınılmaz.  
  
## <a name="end-user-experience"></a>Son kullanıcı deneyimi  
 .NET Framework 4.5 tam yüklemesi yapan bir son kullanıcı, yükleyici kullanımda .NET Framework 4 uygulamaları algılarsa sistemin yeniden başlatılmasını önlemek için fırsatı verilir. Bir ileti, tüm çalışan .NET Framework 4 uygulamalarını listeler ve yüklemeden önce bu uygulamaları kapatın seçeneği sunar. Kullanıcıyı onaylarsa, bu uygulamalar yükleyici tarafından kapatılır ve sistemin yeniden başlatılması önlenmiş olur. Kullanıcı iletiye bir belirli bir süre içinde yanıt vermezse, herhangi bir uygulamayı kapatmadan yüklemesi devam eder.  
  
 Yeniden başlatma Yöneticisi çalışan uygulamalar olsa bile bir sistem yeniden başlatma gerektiren bir durumu kapalı algılarsa, bu ileti görüntülenmez.  
  
 ![Uygulama kapatma çalışmakta olan programların listesi iletişim kutusu.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Zincirleme bir yükleyici kullanarak  
 Uygulamanızla birlikte .NET Framework yeniden dağıtmak istediğiniz, ancak kendi kurulum programı ve UI kullanmak istediğiniz, (bağlayabilirsiniz) .NET Framework Kurulum işlemi, Kurulum işlemine dahil edebilirsiniz. Zincirleme hakkında daha fazla bilgi için bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md). Zincirleme içinde sistem yeniden başlatmalarını azaltmak için Kurulum programınızı kapatmak için uygulamalar listesinde ile .NET Framework yükleyicisi sağlar. Kurulum programınıza gerekir, kullanıcıya bir ileti kutusu gibi bir kullanıcı arabirimi aracılığıyla bu bilgileri sağlayın, kullanıcının yanıt alın ve ardından yanıt .NET Framework yükleyicisi geçirin. Zincirleme bir yükleyici örneği için bkz [nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Zincirleme bir yükleyici kullanıyorsanız ancak uygulamaları kapatmak için kendi ileti kutusunu sağlamayı istemediğiniz, kullanabileceğiniz `/showrmui` ve `/passive` Kurulum Seçenekleri .NET Framework bağladığınızda komut satırında işlemi. Bu seçenekler birlikte kullandığınızda, yükleyici sistemin yeniden başlatılmasını önlemek için kapatılabilir, uygulamaları kapatmak için ileti kutusu gösterir. Tam kullanıcı arabiriminin çalıştığı gibi bu ileti kutusu pasif modda aynı şekilde davranır. Bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md) için .NET Framework yeniden dağıtılabilir için komut satırı seçeneklerinin tam bir set.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](../../../docs/framework/deployment/index.md)
- [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
