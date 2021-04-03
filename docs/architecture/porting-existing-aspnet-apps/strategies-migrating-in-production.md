---
title: Üretimde çalışırken geçiş stratejileri
description: ASP.NET MVC 'den büyük bir uygulamayı tek seferde ASP.NET Core geçiremeyebilir. Bir uygulamayı çalışırken ve mevcut kullanıcılar için üretimde ASP.NET Core geçirmek için bazı stratejiler öğrenin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 9b5d031165773c4da536bdc5478836a1b00436a1
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122735"
---
# <a name="strategies-for-migrating-while-running-in-production"></a>Üretimde çalışırken geçiş stratejileri

Birçok ekibin .NET Core 'a geçirmeyi planlayabilecekleri .NET Framework uygulamaları vardır ancak uygulama, geçişin önemli miktarda tamamlanmasını gerektirdiğinden büyük bir süre gerektirir. Geçiş işlemi parça parça yaptığı sırada orijinal uygulamanın etkin olması gerekir. Uygulamanın eski ve yeni sürümlerinin yan yana birlikte çalışması veya eski sürümün, en az bir şekilde, bu uygulamayı koparmadan yerinde geçirilmesi için bir yol olması gerekir. Takımlar bu hedefleri desteklemek için birçok farklı strateji kullanabilir.

## <a name="refactor-the-net-framework-solution"></a>.NET Framework çözümünü yeniden düzenleme

.NET Core 'a bir .NET Framework uygulamasının bağlantı noktasını, .NET Core ile daha iyi çalışacak şekilde yeniden düzenleme konusunda planladığınız bir başlamak iyi bir yerdir. Bu, tek tek sınıf .NET Standard kitaplıklarının, ASP.NET MVC projelerinizden ve bu sınıf kitaplıklarında çok sayıda mantığa göre güncelleştirilmesi ve bu nesnelerin çok sayıda mantığını güncellemek anlamına gelir. .NET Standard kitaplıklarında bulunan herhangi bir kod, hem .NET Framework hem de .NET Core uygulamalarına (Bu adımın bir geçişin parçası olarak değerli olması) hemen kullanılabilir.

Yeniden düzenleme yaparken, daha iyi yeniden düzenleme temellerini kullandığınızdan emin olun. Örneğin, yeniden düzenlemeye başlamadan önce sistemin ne yaptığını doğrulayan testler oluşturun. Sistemin davranışını değiştirmediğinizi onaylamak için işiniz bittiğinde bu testleri çalıştırın. Güvenebildiğiniz bir otomatik test paketiniz yoksa sisteme karakter seçme testleri eklemeniz gerekebilir.

## <a name="extract-front-end-assets-to-a-cdn"></a>Ön uç varlıkları CDN 'ye Ayıkla

.NET Framework uygulamalarınız, betikler, CSS dosyaları veya görüntüler gibi çok sayıda statik varlık içeriyorsa, bunları ayrı bir CDN 'e geçirebilirsiniz. Ardından, mevcut uygulamayı bu varlıklar için CDN bağlantılarına başvuracak şekilde güncelleştirin. Uygulamayı .NET Core 'a aktardığınızda, bu statik dosyalar geçişin bir parçası olmayacaktır ve yalnızca ASP.NET Core uygulamasındaki CDN 'den başvurmaya devam edersiniz.

## <a name="extract-and-migrate-individual-microservices"></a>Tek tek mikro hizmetleri ayıklama ve geçirme

Büyük .NET Framework uygulamalar, tek tek geçirilebilecek ayrı ön uç sistemlerinden oluşmuş olabilir. Ya da bir mikro hizmet mimarisine geçiş için aday olabilir. bu uygulamalar, bazı mevcut ASP.NET MVC uygulamalarının yeni ASP.NET Core mikro hizmet uygulamalarına kullanıma hazır olmasını sağlar. Mikro hizmetler hakkında daha fazla bilgi için bkz. ilişkili eKitap, [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://aka.ms/microservicesebook).

Örneğin, mevcut uygulamanın kullanıcı oturumu açma ve kayıt ile ilgili olarak kullandığı bir özellikler kümesi olabilir. Bunlar, ASP.NET Core kullanılarak oluşturulup dağıtılabilir ve sonra eski .NET Framework uygulamasıyla tümleştirilebilen ayrı bir mikro hizmete geçirilebilir. Daha sonra, uygulamanın tek bir kullanıcının alışveriş sepetini izlemeye ayrılmış birkaç sayfası olabilir. Bu sayfalar ayrıca kendi ayrı mikro hizmetlerini kullanıma hazır hale gelebilir ve mevcut uygulamayla birlikte tümleştirilir. Bu şekilde, özgün .NET Framework uygulaması üretimde çalışmaya devam eder, ancak modernlanmış .NET Core mikro hizmetlerinden daha fazla ve daha fazlasını sunar.

## <a name="deploy-multiple-versions-of-the-app-side-by-side-in-iis"></a>IIS 'de uygulamanın birden çok sürümünü yan yana dağıtma

Ana bilgisayar üstbilgileri ve yeniden yönlendirmeleri bileşimini kullanarak, var olan bir ASP.NET MVC uygulaması aynı IIS sunucusunda ASP.NET Core bir uygulamayla yan yana çalışacak şekilde yapılandırılabilir. Tek tek denetleyiciler gibi işlevsellik parçalarının ASP.NET Core, yolları ve URL 'Leri, ASP.NET Core Web sitesini veya alt uygulamayı hedefleyecek şekilde IIS 'de eşlenir (IIS sanal dizinleri ASP.NET Core uygulamalarıyla desteklenmez). ASP.NET Core bir uygulama, bir IIS alt uygulaması (alt uygulama) olarak barındırılabilir. Alt uygulamanın yolu, kök uygulamanın URL 'sinin bir parçası haline gelir.

## <a name="apply-the-strangler-pattern"></a>Strangler modelini uygulama

Büyük ASP.NET MVC uygulamaları, işlevselliğin parçalarını artımlı olarak geçirerek yeni bir ASP.NET Core uygulamayla aşamalı olarak değiştirilebilir. Buna bir yaklaşımda, Strangler Vines 'nin adı ve sonunda ağaçları koparmış olan [Strangler deseninin](/azure/architecture/patterns/strangler)adı verilir. Bu yaklaşım, ilk olarak mevcut çözümün en üstünde bir façlade katmanını uygulamaya dayanır. Bu façlade, soruna yönelik yeni yaklaşım veya bir API ağ geçidi gibi raf dışı bir çözüm kullanılarak oluşturulmalıdır.

Façlade olduktan sonra, bunun bir kısmını yeni bir ASP.NET Core uygulamasına yönlendirebilirsiniz. .NET Core 'a özgün .NET Framework uygulamasının daha fazlasını yaptığınızda, façlade katmanını uygun şekilde güncelleştirmeye devam edersiniz ve bu da daha fazla façladem işlevinin yeni sisteme gönderilmesini sağlar. Şekil 3-5, zaman içinde yabangler deseninin ilerlemesini gösterir.

![Şekil 3-5](media/Figure3-5.png)

**Şekil 3-5.** Zaman içinde Yabangler deseninin.

Sonuç olarak, façlade katmanının tamamı yeni, modern uygulamaya karşılık gelir. Bu noktada, hem eski sistem hem de yüz katman devre dışı bırakılabilir.

## <a name="multi-targeting-approaches"></a>Çoklu hedefleme yaklaşımları

.NET Framework hedef olan büyük uygulamalar, her bir çerçeve için Çoklu hedefleme ve ayrı kod yolları kullanılarak zaman içinde ASP.NET Core geçirilebilir. Örneğin, her iki ortamda da çalışması gereken kod, farklı işlevler uygulamak veya .NET Framework .NET Core 'da çalıştırıldığında farklı bağımlılıklar kullanmak için [Önişlemci `#if` ](../../csharp/language-reference/preprocessor-directives.md#conditional-compilation) yönergeleri ile değiştirilebilir. Başka bir seçenek de proje dosyalarını, hedeflenen Framework 'ü temel alan farklı dosya kümelerini içerecek şekilde değiştirmektir. Proje dosyaları, `*.core.cs` hedeflenen çerçeveye göre farklı kaynak dosya kümelerini dahil etmek için gibi farklı glob desenleri kullanabilir. Genellikle yalnızca birden çok Web uygulaması tarafından kullanılacak kitaplıklar için bu yaklaşımı takip edersiniz. Web uygulamalarının kendisi için, iki ayrı projenin olması genellikle daha iyidir.

Bu teknikler, tek bir ortak kod temelinin, yeni işlevsellik eklendiğinde ve (bazı parçalar) .NET Core kullanımı dışında tutulmasını sağlar.

## <a name="summary"></a>Özet

Genellikle, büyük ASP.NET MVC ve Web API uygulamaları her seferinde ASP.NET Core değil, ancak zaman içinde artımlı olarak geçirilir. Bu bölümde, bu artımlı geçişi gerçekleştirmek için çeşitli stratejiler sunulmaktadır. Kuruluşunuz ve uygulamanız için en iyi şekilde çalışacak olan birini seçin.

## <a name="references"></a>Başvurular

- [.NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari](https://aka.ms/microservicesebook)
- [eShopOnContainers başvuru mikro hizmetleri uygulaması](https://github.com/dotnet-architecture/eShopOnContainers)
- [IIS ile Windows üzerinde ASP.NET Core barındırma](/aspnet/core/host-and-deploy/iis/)
- [Strangler düzeni](/azure/architecture/patterns/strangler)

>[!div class="step-by-step"]
>[Önceki](understand-update-dependencies.md) 
> [Sonraki](example-migration-eshop.md)
