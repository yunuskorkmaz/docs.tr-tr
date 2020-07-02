---
title: .NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
description: .NET 4,5 yüklemeleri sırasında sistem yeniden başlatmalarının azaltılmasını öğrenin. .NET 4,5 yüklemesi sırasında bir .NET 4 uygulaması kullanılıyorsa yeniden başlatma gerekebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: bfde0c2f7297c048ba70062918e2281afbccf391
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618213"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma
.NET Framework 4,5 yükleyicisi, yükleme sırasında mümkün olduğunda sistemin yeniden başlatılmasını engellemek için [yeniden başlatma yöneticisini](/windows/win32/rstmgr/about-restart-manager) kullanır. Uygulama kurulum programınız .NET Framework yüklerse, bu özellikten yararlanmak için yeniden başlatma yöneticisiyle arabirim oluşturabilir. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework 4,5 Yükleyicisinden Ilerleme durumu alma](how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Yeniden başlatma nedenleri  
 .NET Framework 4,5 yüklemesi, yükleme sırasında bir .NET Framework 4 uygulaması kullanılıyorsa sistemin yeniden başlatılmasını gerektirir. Bunun nedeni 4,5 .NET Framework .NET Framework 4 dosyalarını değiştirmesi ve yükleme sırasında bu dosyaların kullanılabilir olmasını gerektirmesidir. Çoğu durumda, yeniden başlatma, kullanımda olan preemptively algılama ve closing.NET Framework 4 uygulamaları tarafından engellenebilir. Ancak bazı sistem uygulamaları kapatılmamalıdır. Bu durumlarda yeniden başlatmanın önlenemez.  
  
## <a name="end-user-experience"></a>Son Kullanıcı deneyimi  
 .NET Framework 4,5 ' nin tam yüklemesini yapan bir son kullanıcıya, yükleyicinin kullanımda olan .NET Framework 4 uygulama algılaması durumunda sistemin yeniden başlatılmasını önleyin. Bir ileti, çalışan tüm .NET Framework 4 uygulamalarını listeler ve yüklemeden önce bu uygulamaları kapatma seçeneğini sağlar. Kullanıcı onayladığında, bu uygulamalar yükleyici tarafından kapatılır ve sistemin yeniden başlatılması önlenmiş olur. Kullanıcı belirli bir süre içinde iletiye yanıt vermezse, yükleme hiçbir uygulamayı kapatmadan devam eder.  
  
 Yeniden başlatma Yöneticisi, çalışan uygulamalar kapalı olsa bile sistemin yeniden başlatılmasını gerektiren bir durum algılarsa, ileti görüntülenmez.  
  
 ![Şu anda çalışmakta olan programları listeleyerek uygulamayı kapat iletişim kutusu.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Zincir yükleyici kullanma  
 .NET Framework uygulamanıza yeniden dağıtmak istiyorsanız, ancak kendi kurulum programınızı ve Kullanıcı arabirimini kullanmak istiyorsanız, kurulum sürecinize .NET Framework kurulum işlemini ekleyebilirsiniz. Zincirleme yüklemeleri hakkında daha fazla bilgi için bkz. [geliştiriciler Için dağıtım kılavuzu](deployment-guide-for-developers.md). Zincirleme yüklemedeki sistem yeniden başlatmaları azaltmak için .NET Framework yükleyicisi, kapatılacak uygulamaların listesini kullanarak kurulum programınızı sağlar. Kurulum programınızın bu bilgileri kullanıcıya ileti kutusu gibi bir kullanıcı arabirimi aracılığıyla sağlaması, kullanıcının yanıtını alması ve sonra yanıtı .NET Framework yükleyiciye geri geçirmesi gerekir. Bir zincir yükleyici örneği için, [nasıl yapılır: .NET Framework 4,5 Yükleyicisinden Ilerleme durumunu alma](how-to-get-progress-from-the-dotnet-installer.md)makalesine bakın.  
  
 Bir zincir yükleyici kullanıyorsanız, ancak uygulamaları kapatmak için kendi ileti kutusunu sağlamak istemiyorsanız, `/showrmui` `/passive` .NET Framework kurulum işlemini zincirleyebilirsiniz komut satırındaki ve seçeneklerini kullanabilirsiniz. Bu seçenekleri birlikte kullandığınızda, yükleyici, sistemin yeniden başlatılmasını önlemek için kapatıladıklarında uygulamaları kapatmak için ileti kutusunu gösterir. Bu ileti kutusu, tam kullanıcı arabirimi altında olduğu gibi pasif modda aynı şekilde davranır. Yeniden dağıtılabilir .NET Framework için komut satırı seçeneklerinin tam kümesini görmek üzere [geliştiriciler Için dağıtım kılavuzu](deployment-guide-for-developers.md) ' na bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](index.md)
- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](how-to-get-progress-from-the-dotnet-installer.md)
