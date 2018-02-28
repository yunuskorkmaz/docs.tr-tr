---
title: "Roslyn .NET çözümleyiciler - temel"
description: "Sorunları bulmak ve bu sorunları düzeltmelerin önerilen temel Roslyn Çözümleyicileri hakkında bilgi edinin."
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a>Çözümleyiciler Roslyn dayalı

Roslyn tabanlı çözümleyiciler sorunları bulmak ve düzeltmeleri önermek için projenizin kaynak kodu çözümlemek için .NET derleyici SDK'sı (Roslyn API) kullanın. Farklı sınıflar API Uyumluluk için güvenlik sorunlarının hatalara neden olabilecek uygulamalar arasında değişen sorunların farklı çözümleyiciler arayın.

Çözümleyiciler Roslyn tabanlı hem de etkileşimli ve derlemeleri sırasında çalışır. Çözümleyici Visual Studio'da veya komut satırı derlemeleri farklı bir Rehber sağlanır.

Visual Studio'da kodu düzenlerken sorunları tetiklemek kod oluşturur oluşturmaz olası sorunları yakalama değişiklik yapmak gibi çözümleyiciler çalıştırın. Tüm sorunları, herhangi bir sorun altında dalgalı çizgiler ile vurgulanır. Visual Studio bir ampul görüntüler ve üzerine tıkladığınızda Çözümleyicisi bu sorunun olası düzeltmeler önerir. Projeyi derlerken Visual Studio'da ya da komut satırından, tüm kaynak kodunu analiz edilir ve Çözümleyicisi olası sorunları tam bir listesini sağlar. Aşağıdaki şekilde bir örnek gösterilmektedir.

![framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

Roslyn tabanlı çözümleyiciler hatalar, uyarılar ve bilgiler sorunun önem derecesine göre olarak olası sorunları bildirin.

Projenizdeki NuGet paketlerini Roslyn tabanlı çözümleyiciler yükleyin. Yapılandırılmış Çözümleyicileri ve her Çözümleyicisi için herhangi bir ayarı geri ve bu proje için her geliştiricinin makinede çalıştırın.

> [!NOTE]
> Roslyn tabanlı Çözümleyicileri için kullanıcı deneyimi kod analiz kitaplıkları'nın eski sürümleri FxCop ve güvenlik analiz araçları, ister kullanılandan farklıdır.  Açıkça Roslyn tabanlı çözümleyiciler çalışması gerekmez. Visual Studio'da "Çözümle" menüsünden "Kod Analizi Çalıştır" menü öğelerini kullanmasına gerek yoktur. Çalışırken Roslyn tabanlı çözümleyiciler asychronously çalıştırın. 

## <a name="more-information-on-specific-analyzers"></a>Belirli çözümleyicileri hakkında daha fazla bilgi

Aşağıdaki çözümleyiciler, bu bölümde ele alınmıştır:

[API Çözümleyicisi](api-analyzer.md): Bu Çözümleyicisi kodunuzu olası uyumluluk riskler açısından inceler veya kullanım dışı API'lerinin kullanır.    
[Framework Çözümleyicisi](framework-analyzer.md): .NET Framework uygulamaları yönelik yönergeleri izleyen emin olmak için kodunuzu bu Çözümleyicisi inceler. Bu kurallar birkaç tabanlı güvenlik önerileri içerir.
