---
title: .NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: 6261a883e7b99b7fd38da2a17ab4820c81552506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716425"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
.NET Framework 4.5 yükleyici, yükleme sırasında mümkün olduğunda sistemin yeniden başlatılmasını önlemek için [Yeniden Başlat Yöneticisi'ni](/windows/win32/rstmgr/about-restart-manager) kullanır. Uygulama kurulum programınız .NET Framework'ü yüklüyorsa, bu özellikten yararlanmak için Yeniden Başlat Yöneticisi ile arayüz kurabilir. Daha fazla bilgi [için bkz: .NET Framework 4.5 Yükleyiciden İlerleme Alın.](how-to-get-progress-from-the-dotnet-installer.md)  
  
## <a name="reasons-for-a-restart"></a>Yeniden Başlatma Nedenleri  
 .NET Framework 4.5 yüklemesi, yükleme sırasında bir .NET Framework 4 uygulaması kullanılıyorsa bir sistemin yeniden başlatılmasını gerektirir. Bunun nedeni,.NET Framework 4.5'in .NET Framework 4 dosyalarının yerini alması ve bu dosyaların yükleme sırasında kullanılabilir olmasını gerektirmesidir. Çoğu durumda, yeniden başlatma önceden algılanması ve kullanılmakta olan Framework 4 uygulamaları closing.NET önlenebilir. Ancak, bazı sistem uygulamaları kapatılmamalıdır. Bu gibi durumlarda, yeniden başlatma önlenemez.  
  
## <a name="end-user-experience"></a>Son Kullanıcı Deneyimi  
 .NET Framework 4.5'in tam yüklemesini yapan bir son kullanıcıya, yükleyici .NET Framework 4 uygulamalarını kullanırken algılarsa sistemin yeniden başlatılmasını önleme fırsatı verilir. İleti, çalışan tüm .NET Framework 4 uygulamalarını listeler ve yüklemeden önce bu uygulamaları kapatma seçeneği sunar. Kullanıcı onaylarsa, bu uygulamalar yükleyici tarafından kapatılır ve sistemin yeniden başlatılması önlenir. Kullanıcı iletiyi belirli bir süre içinde yanıtvermezse, yükleme herhangi bir uygulamayı kapatmadan devam eder.  
  
 Yeniden Başlat Yöneticisi, çalışan uygulamalar kapalı olsa bile sistemin yeniden başlatılmasını gerektiren bir durum algılarsa, ileti görüntülenmez.  
  
 ![Uygulamayı Kapat iletişim kutusu şu anda çalışan programları listeler.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Zincirli Yükleyici Kullanma  
 .NET Framework'ü uygulamanızla yeniden dağıtmak istiyorsanız, ancak kendi kurulum programınızı ve UI'nizi kullanmak istiyorsanız, .NET Framework kurulum işlemini kurulum işleminize (zincirleme) ekleyebilirsiniz. Zincirli yüklemeler hakkında daha fazla bilgi için [Geliştiriciler için Dağıtım Kılavuzu'na](deployment-guide-for-developers.md)bakın. Zincirleme yüklemelerde sistemin yeniden başlatılmasını azaltmak için,.NET Framework yükleyicisi kurulum programınızı kapatmanız gereken uygulamaların listesini sağlar. Kurulum programınız bu bilgileri ileti kutusu gibi bir kullanıcı arabirimi aracılığıyla kullanıcıya sağlamalı, kullanıcının yanıtını almalı ve yanıtı .NET Framework yükleyicisine geri aktarmalıdır. Zincirlenmiş bir yükleyici örneği için [bkz.](how-to-get-progress-from-the-dotnet-installer.md)  
  
 Zincirli bir yükleyici kullanıyorsanız, ancak uygulamaları kapatmak için kendi ileti kutunuzu sağlamak istemiyorsanız, .NET Framework kurulum işlemini zincirlediğinizde komut satırındaki `/showrmui` seçenekleri `/passive` kullanabilirsiniz. Bu seçenekleri birlikte kullandığınızda, yükleyici, sistemin yeniden başlatılmasını önlemek için kapatılabilirse uygulamaları kapatmak için ileti kutusunu gösterir. Bu ileti kutusu, tam kullanıcı arabirimi altında olduğu gibi pasif modda da aynı şekilde çalışır. .NET Framework yeniden dağıtılabilir için komut satırı seçeneklerinin tamamı için [Geliştiriciler için Dağıtım Kılavuzu'na](deployment-guide-for-developers.md) bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](index.md)
- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](how-to-get-progress-from-the-dotnet-installer.md)
