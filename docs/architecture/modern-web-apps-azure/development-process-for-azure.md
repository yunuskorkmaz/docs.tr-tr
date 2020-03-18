---
title: Azure için geliştirme işlemi
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Azure için geliştirme süreci
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 7a641c1b6665af6e9e78ef182174b360041d74aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450055"
---
# <a name="development-process-for-azure"></a>Azure için geliştirme işlemi

> _"Bulutla, bireyler ve küçük işletmeler parmaklarını şıklatıp anında kurumsal sınıf hizmetler kurabilir."_  
> _- Roy Stephan_

## <a name="vision"></a>Görsel

> *Visual Studio veya dotnet CLI ve Visual Studio Code'u veya seçtiğiniz editörü kullanarak iyi tasarlanmış ASP .NET Core uygulamalarını istediğiniz gibi geliştirin.*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core uygulamaları için geliştirme ortamı

### <a name="development-tools-choices-ide-or-editor"></a>Geliştirme araçları seçenekleri: IDE veya düzenleyici

İster tam ve güçlü bir IDE ister hafif ve çevik bir düzenleyici tercih edin, Microsoft, Core uygulamaları ASP.NET geliştirirken sizi ele almıştır.

**Görsel Stüdyo 2019.** Visual Studio 2019, ASP.NET Core için uygulama geliştirmek için sınıfının en iyisi IDE'dir. Geliştirici üretkenliğini artıran bir dizi özellik sunar. Uygulamayı geliştirmek, ardından performansını ve diğer özelliklerini analiz etmek için kullanabilirsiniz. Tümleşik hata ayıklayıcı, kod yürütmeyi duraklatmanızı ve çalışırken anında kod üzerinden ileri geri adım atmanızı sağlar. Yerleşik test koşucusu, testlerinizi ve sonuçlarını düzenlemenizi sağlar ve hatta kodlama yaparken canlı birim testi gerçekleştirebilirsiniz. Live Share'i kullanarak, kod oturumunuzu ağ üzerinden sorunsuz bir şekilde paylaşarak diğer geliştiricilerle gerçek zamanlı olarak işbirliği yapabilirsiniz. Hazır olduğunuzda Visual Studio, uygulamanızı Azure'da veya barındırabileceğiniz her yerde yayınlamak için ihtiyacınız olan her şeyi içerir.

[Visual Studio 2019’u İndirin](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code ve dotnet CLI** (Mac, Linux ve Windows için Çapraz Platform Araçları). Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyici tercih ederseniz, Microsoft Visual Studio Code ve dotnet CLI'yi kullanabilirsiniz. Bu ürünler, geliştirici iş akışını kolaylaştıran basit ama sağlam bir deneyim sağlar. Ayrıca, Visual Studio Code editör\# içinde intellisense ve kısayol görevleri sağlayarak, C ve web geliştirme uzantıları destekler.

[.NET Çekirdek SDK'yı indirin](https://dotnet.microsoft.com/download)

[Visual Studio Kodu İndir](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure barındırılan ASP.NET Core uygulamaları için geliştirme iş akışı

Uygulama geliştirme yaşam döngüsü her geliştiricinin makinesinden başlar, uygulamayı tercih ettikleri dili kullanarak kodlar ve yerel olarak test eder. Geliştiriciler tercih ettikleri kaynak denetim sistemini seçebilir ve bir yapı sunucusu kullanarak veya yerleşik Azure özelliklerini temel alan Sürekli Tümleştirme (CI) ve/veya Sürekli Teslim/Dağıtım (CD) yapılandırabilir.

CI/CD kullanarak ASP.NET Bir Çekirdek uygulaması geliştirmeye başlamak için Azure DevOps Hizmetlerini veya kuruluşunuzun kendi Team Foundation Server'ını (TFS) kullanabilirsiniz.

### <a name="initial-setup"></a>İlk kurulum

Uygulamanız için bir sürüm ardışık hattı oluşturmak için uygulama kodunuzu kaynak denetiminde olmanız gerekir. Yerel bir depo ayarlayın ve bir takım projesinde uzak bir depoya bağlayın. Aşağıdaki talimatları izleyin:

- [Kodunuzu Git ve Visual Studio ile paylaşın](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) veya

- [Kodunuzu TFVC ve Visual Studio ile paylaşın](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Uygulamanızı dağıtacağınız bir Azure Uygulama Hizmeti oluşturun. Azure portalındaki Uygulama Hizmetleri bıçağına giderek bir Web Uygulaması oluşturun. +Ekle'yi tıklatın, Web Uygulaması şablonu seçin, Oluştur'u tıklatın ve bir ad ve diğer ayrıntılar sağlayın. Web uygulamasına {name}.azurewebsites.net adresinden erişilecektir.

![AzureWebApp](./media/image10-2.png)

**Şekil 10-1.** Azure Portalı'nda yeni bir Azure Uygulaması Hizmeti Web Uygulaması oluşturma.

Yeni kod projenin kaynak denetim deposuna adadığında CI yapı işleminiz otomatik bir yapı gerçekleştirir. Bu, kodun oluşturduğu (ve ideal olarak otomatik testleri geçtiği) ve dağıtılabilir olabileceği ne kadar acil geri bildirim sağlar. Bu CI yapısı bir web dağıtım paketi artifakı üretecek ve CD işleminiz tarafından tüketim için yayımlayacaktır.

[CI yapı işleminizi tanımlayın](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Ekibinizdeki biri yeni kod işlediğinde sistemin bir yapı yığması için sürekli tümleştirmeyi etkinleştirdiğinizden emin olun. Yapıyı test edin ve yapılarından biri olarak bir web dağıtım paketi ürettiğini doğrulayın.

Bir yapı başarılı olduğunda, CD işleminiz CI yapınızın sonuçlarını Azure web uygulamanıza dağıtacaktır. Bunu yapılandırmak için, Azure Uygulama Hizmetinize dağıtılacak bir *Sürüm*oluşturur ve yapılandırırsınız.

[CD sürüm işleminizi tanımlayın](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

CI/CD ardışık hattınız yapılandırıldıktan sonra, web uygulamanızda güncellemeler yapabilir ve bunları dağıtılmak üzere kaynak denetimine bağlayabilirsiniz.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Azure barındırılan ASP.NET Çekirdek uygulamaları geliştirmek için iş akışı

Azure hesabınızı ve CI/CD işleminizi yapılandırdıktan sonra, Azure barındırılan ASP.NET Core uygulamalarını geliştirmek kolaydır. Aşağıda, Şekil 10-2'de gösterildiği gibi Azure App Service'de Web Uygulaması olarak barındırılan bir ASP.NET Core uygulaması oluşturmak için genellikle attığınız temel adımlar verebilirsiniz.

![EndToEndDevDeployİş Akışı](./media/image10-3.png)

**Şekil 10-2.** ASP.NET Core uygulamaları oluşturmak ve Azure'da barındırmak için adım adım iş akışı

#### <a name="step-1-local-dev-environment-inner-loop"></a>1. Adım. Yerel dev ortamı iç döngü

Azure'a dağıtım için ASP.NET Core uygulamanızı geliştirmek, uygulamanızı başka türlü geliştirmekten farklı değildir. Visual Studio 2017 veya dotnet CLI ve Visual Studio Code veya tercih ettiğiniz düzenleyici olsun, rahat ettiğiniz yerel geliştirme ortamını kullanın. Değişikliklerinizi paylaşılan kaynak denetim deponuza itmeye hazır olana kadar kod yazabilir, değişikliklerinizi çalıştırabilir ve hata ayıklayabilir, otomatik testler çalıştırabilir ve yerel taahhütleri kaynak denetimine geçirebilirsiniz.

#### <a name="step-2-application-code-repository"></a>2. Adım Uygulama kodu deposu

Kodunuzu ekibinizle paylaşmaya hazır olduğunuzda, değişikliklerinizi yerel kaynak deposunuzdan ekibinizin paylaşılan kaynak deposuna itmelisiniz. Özel bir dalda çalışıyorsanız, bu adım genellikle kodunuzu paylaşılan bir dala birleştirmeyi içerir (belki de çekme [isteği](https://docs.microsoft.com/azure/devops/git/pull-requests)yoluyla).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>3. Adım Build Server: Sürekli tümleştirme. inşa, test, paket

Paylaşılan uygulama kodu deposuna yeni bir işleme yapıldığında yapı sunucusunda yeni bir yapı tetiklenir. CI işleminin bir parçası olarak, bu yapı uygulamayı tam olarak derlemeli ve her şeyin beklendiği gibi çalıştığını doğrulamak için otomatik testler çalıştırmalıdır. CI işleminin sonucu, dağıtıma hazır web uygulamasının paketlenmiş bir sürümü olmalıdır.

#### <a name="step-4-build-server-continuous-delivery"></a>4. Adım. Build Server: Sürekli teslimat

Bir yapı başarılı olduktan sonra, CD işlemi üretilen yapı yapılarını alır. Bu bir web dağıtım paketi içerecektir. Yapı sunucusu bu paketi Azure Uygulama Hizmeti'ne dağıtarak mevcut tüm hizmetleri yeni oluşturulan hizmetle değiştirir. Genellikle bu adım bir evreleme ortamını hedefler, ancak bazı uygulamalar cd işlemi aracılığıyla doğrudan üretime dağıtılır.

#### <a name="step-5-azure-app-service-web-app"></a>5. Adım. Azure App Service Web App

Dağıtıldıktan sonra, ASP.NET Core uygulaması bir Azure App Service Web Uygulaması kapsamında çalışır. Bu Web Uygulaması Azure Portalı kullanılarak izlenebilir ve daha da yapılandırılabilir.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>6. Adım. Üretim izleme ve tanılama

Web Uygulaması çalışırken, uygulamanın durumunu izleyebilir ve tanılama ve kullanıcı davranışı verilerini toplayabilirsiniz. Application Insights Visual Studio'ya dahildir ve ASP.NET uygulamalar için otomatik enstrümantasyon sunar. Kullanım, özel durumlar, istekler, performans ve günlükler hakkında bilgi sağlayabilir.

## <a name="references"></a>Başvurular

**ASP.NET Çekirdek Uygulamanızı Oluşturun ve Azure'a Dağıtın**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Önceki](test-asp-net-core-mvc-apps.md)
>[Sonraki](azure-hosting-recommendations-for-asp-net-web-apps.md)
