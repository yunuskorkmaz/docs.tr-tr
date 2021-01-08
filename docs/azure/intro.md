---
title: Azure ve .NET ile çalışmaya başlama
description: Azure ve .NET hakkında bilmeniz gereken temel bilgileri öğrenin.
ms.date: 06/20/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b5766012b77da88ae9a696939b6e498ebc421522
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025048"
---
# <a name="introduction-to-azure-and-net"></a>Azure ve .NET’e giriş

## <a name="what-is-azure"></a>Azure nedir?

Azure, modern uygulamalar oluşturma işlemini basitleştirmek için tasarlanan bir bulut platformudur.  Uygulamalarınızı tamamen Azure 'da barındırmaya veya şirket içi uygulamalarınızı Azure hizmetleriyle genişletmenize bakılmaksızın Azure, ölçeklenebilir, güvenilir ve sürdürülebilir uygulamalar oluşturmanıza yardımcı olur.  Visual Studio ve Visual Studio Code ve kapsamlı bir SDK Kitaplığı gibi zaten kullandığınız araçlarda kapsamlı destek sayesinde Azure, .NET Developer 'ı başlangıçtan hemen itibaren üretken hale getirmek için tasarlanmıştır.

## <a name="application-development-scenarios-on-azure"></a>Azure 'da uygulama geliştirme senaryoları

Gereksinimlerinize göre farklı yollarla Azure 'u uygulamanıza ekleyebilirsiniz.

- **Azure 'Da uygulama barındırma-** Azure, tüm uygulama yığınınızı Web uygulamalarından ve API 'lerden depolama hizmetlerine veritabanlarına barındırabilir. Azure, tam olarak yönetilen hizmetlerden sanal makinelere kapsayıcılara kadar çeşitli barındırma modellerini destekler. Tam olarak yönetilen Azure hizmetlerini kullanırken uygulamalarınız, Azure 'da yerleşik olarak bulunan ölçeklenebilirlik, yüksek kullanılabilirlik ve güvenliğin avantajlarından yararlanabilir.

- **Uygulamalardan bulut hizmetlerini tüketme-** Mevcut uygulamalar, yeteneklerini genişletmek için Azure hizmetlerini birleştirebilir.  Bu, [azure bilişsel arama](/azure/search/search-what-is-azure-search)ile tam metin arama özelliği eklemenin yanı sıra Azure bilişsel [Hizmetler](/azure/cognitive-services/)ile, uygulama gizli dizilerini [Azure Key Vault](/azure/key-vault/) güvenli bir şekilde depolamayı veya görme, konuşma ve dil özelliklerine sahip özellikleri eklemeyi içerebilir.  Bu hizmetler Azure tarafından tamamen yönetilir ve geçerli uygulama mimarinizi veya dağıtım modelinizi değiştirmeden uygulamanıza kolayca eklenebilir.

- **Modern sunucusuz mimariler-** Azure Işlevleri, olay odaklı iş akışlarını işlemek, HTTP isteklerine yanıt verip vermediğini, blob depolamada dosya karşıya yüklemelerini işlemeyi veya bir kuyruktaki olayları işlemeyi basitleştirir.  Yalnızca, sunucu veya çerçeve kodu hakkında endişelenmeden olaylarınızı işlemek için gerekli olan kodu yazarsınız.  Ayrıca, en zorlu tümleştirme sorunlarınızı ortadan kaldırmak için, diğer Azure ve üçüncü taraf hizmetlere 250 bağlayıcıdan faydalanabilirsiniz.

## <a name="access-azure-services-from-net-applications"></a>.NET uygulamalarından Azure hizmetlerine erişme

Uygulamanızın Azure 'da veya şirket içinde barındırılıp barındırılmayacağı, **.net Için Azure SDK** aracılığıyla birçok Azure hizmetine erişim sağlanır.  .NET için Azure SDK, bir dizi NuGet paketi olarak sağlanır ve hem .NET Core (2,1 ve üzeri) hem de .NET Framework (4.6.1 ve üzeri) uygulamalarda kullanılabilir. .NET için Azure SDK, doğru NuGet paketini yüklemek, bir istemci nesnesini örnekleyip uygun yöntemleri çağırmak kadar kolayca uygulamanıza Azure hizmetleri ekleme olanağı sunar. .NET için Azure SDK hakkında daha fazla bilgi [.net Için Azure SDK 'Ya genel bakış](./sdk/azure-sdk-for-dotnet.md)bölümünde bulunabilir.

![.NET uygulamalarının Azure hizmetlerine erişmek için Azure SDK 'sını nasıl kullandığını gösteren diyagram](./media/azure-sdk-for-dotnet-overview.png)

## <a name="next-steps"></a>Sonraki adımlar

Ardından, .NET geliştirme için en [yaygın olarak kullanılan Azure hizmetleri](./key-azure-services.md) hakkında bilgi edinin.
