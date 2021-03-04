---
title: ASP.NET Core 2,1 ' ye geçir
description: .NET Framework çalışma zamanı hedefleme 'yi desteklemeye yönelik son .NET Core sürümü, .NET Core 2,1 ' ye geçiş, bazı uygulama geçiş planlarında ara adım olarak anlamlı midir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0c478ae194c6d9118bfbca73f8933d7623246e2c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105896"
---
# <a name="migrate-to-aspnet-core-21"></a>ASP.NET Core 2,1 ' ye geçir

ASP.NET Core 2,1, hem .NET Core hem de .NET Framework çalışma zamanlarını desteklemek için desteklenen tek .NET Core sürümü olduğu için ilginç bir sürümdür. Bu nedenle, uygulamanın tüm parçalarını aynı anda .NET Core 'a yükseltmeye kıyasla bazı uygulamalar için daha kolay bir yükseltme yolu sunabilir. LTS sürümü olarak, .NET Core 2,1 desteği 2021 Ağustos 'Tan itibaren devam edecektir. .NET Framework üzerinde çalışan ASP.NET Core 2,1 desteği, temeldeki .NET Framework desteklendiği sürece devam eder.

## <a name="should-apps-run-on-net-framework-with-aspnet-core-21"></a>Uygulamalar ASP.NET Core 2,1 ile .NET Framework çalışır olmalıdır

ASP.NET Core 2,2 ve önceki sürümleri hem .NET Core hem de .NET Framework çalışma zamanları destekleniyor. Bir uygulamanın bazılarını veya tümünü, .NET Core 'a tamamen geçebilmeniz için bir atlama Stone olarak ASP.NET Core 2,1 'e geçirmek mantıklı midir? Uygulamalar veya uygulamaların alt kümeleri, ASP.NET Core kullanımı sırasında ön uç ASP.NET mantığını görebilir ve iş mantığı ve altyapı tüketimine yönelik .NET Framework kitaplıklarını kullanmaya devam edebilir. Bu yaklaşım çok iş mantığı olmayan görece ince bir kullanıcı arabirimi katmanı ve sınıf kitaplıklarında çok daha büyük bir işlevsellik kümesi olduğunda anlamlı olabilir.

Yalnızca ön uç Web katmanını ASP.NET Core 2,1 ' ye taşımanın başlıca avantajı, mevcut .NET sınıf kitaplıklarının ilk geçiş sırasında olduğu gibi kalacağından emin olur. Bunlar, diğer .NET uygulamaları tarafından sürekli kullanılıyor olabilir veya yalnızca .NET Core 'a planlı tam geçişin ilk yinelemesi kapsamında olması gerekmez. Büyük uygulamalar için ilk geçişin kapsamını azaltmak, genellikle .NET Core 'a giden bir bağlantı noktası olan, istenen bitiş durumuna doğru bir şekilde işlem gören artımlı hedefler sağlamaya yardımcı olur.

Bu stratejiyi kullanamayacak mevcut bir uygulamanız varsa, işleme hazırlanmasına yardımcı olmak için bazı şeyler, iş mantığı, veri erişimi ve diğer kullanıcı arabirimi dışı mantığı ASP.NET projelerinden ve mümkün olduğunca ayrı sınıf kitaplıklarına taşımaktır. Ayrıca, sisteminizin otomatik test kapsamınız varsa, davranışın geçişten önce ve sonra tutarlı olmaya devam ettiğini doğrulayabilmeniz için bu da size yardımcı olur.

Uygulamanız, Web uygulamasının tamamını aynı anda geçiremeyeceğiniz kadar büyükse ve yeni ASP.NET Core uygulamayı mevcut ASP.NET uygulamasıyla yan yana dağıtabilmeniz gerekiyorsa, bunu başarmak için kullanılabilecek dağıtım stratejileri vardır. Bunlar [Bölüm 5: dağıtım senaryolarında](deployment-scenarios.md)ele alınmıştır.

ASP.NET Core 2,1 ' nin, .NET Core 'un .NET Framework çalıştırmayı ve .NET Framework kitaplıklarını kullanmayı destekleyen son LTS sürümü olduğunu aklınızda bulundurun. Bu yayın yakında desteklenecek, ancak .NET Framework ASP.NET Core 2,1 .NET Framework (.NET Core 2,1 desteği sona erdikten sonra bile). Daha fazla bilgi için [.NET Framework ASP.NET Core 2,1](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.

## <a name="references"></a>Başvurular

[ASP.NET 'den ASP.NET Core 2,1 'ye geçiş](/aspnet/core/migration/proper-to-2x/?preserve-view=true&view=aspnetcore-2.1)

>[!div class="step-by-step"]
>[Önceki](migration-considerations.md) 
> [Sonraki](choose-net-core-version.md)
