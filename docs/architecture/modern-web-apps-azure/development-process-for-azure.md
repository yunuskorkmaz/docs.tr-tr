---
title: Azure için geliştirme işlemi
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın Azure için geliştirme işlemi
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 7a641c1b6665af6e9e78ef182174b360041d74aa
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450055"
---
# <a name="development-process-for-azure"></a>Azure için geliştirme işlemi

> _"Bulut sayesinde, bireyler ve küçük işletmeler parmaklarını yeniden düzenleyebilir ve kurumsal sınıf Hizmetleri anında ayarlayabilir."_  
> _-Roy Stephan_

## <a name="vision"></a>Görsel

> *Visual Studio veya DotNet CLı ve Visual Studio Code ya da seçtiğiniz düzenleyiciyi kullanarak istediğiniz şekilde iyi tasarlanmış ASP .NET Core Uygulamaları geliştirin.*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core uygulamalar için geliştirme ortamı

### <a name="development-tools-choices-ide-or-editor"></a>Geliştirme araçları seçimleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da hafif ve çevik bir düzenleyici tercih etmeksizin, Microsoft ASP.NET Core uygulamalar geliştirirken kapsanmış olursunuz.

**Visual Studio 2019.** Visual Studio 2019, ASP.NET Core yönelik uygulamalar geliştirmek için sınıfının en iyisi IDE 'dir. Geliştirici üretkenliğini artıran özelliklerin bir konağını sunar. Uygulamayı geliştirmek için kullanabilir ve sonra performansını ve diğer özelliklerini çözümleyebilirsiniz. Tümleşik hata ayıklayıcı, kod yürütmeyi duraklatmanıza ve çalışırken kod aracılığıyla anında ve geriye ilerlemenizi sağlar. Yerleşik Test Çalıştırıcısı, testlerinizi ve sonuçlarını düzenlemenizi sağlar ve kodlarken bile canlı birim testi gerçekleştirebilir. Live Share kullanarak, diğer geliştiricilerle gerçek zamanlı işbirliği yapabilir ve kod oturumunuzu ağ üzerinden sorunsuzca paylaştırın. Ve hazırsanız, Visual Studio, uygulamanızı Azure 'da yayımlamak için gereken her şeyi veya barındırmanızı sağlar.

[Visual Studio 2019’u İndirin](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code ve DotNet CLI** (Mac, Linux ve Windows için platformlar arası araçlar). Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyiciyi tercih ediyorsanız, Microsoft Visual Studio kodu ve DotNet CLı kullanabilirsiniz. Bu ürünler, geliştirici iş akışını kolaylaştıran basit ancak sağlam bir deneyim sağlar. Ayrıca, Visual Studio Code, düzenleyici içinde IntelliSense ve kısayol görevleri sağlayan C\# ve Web geliştirme için uzantıları destekler.

[.NET Core SDK indirin](https://dotnet.microsoft.com/download)

[Visual Studio Code indir](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure 'da barındırılan ASP.NET Core uygulamaları için geliştirme iş akışı

Uygulama geliştirme yaşam döngüsü, her geliştiricinin makinesinden başlar, tercih ettiğiniz dil kullanılarak uygulamayı kodlamalarını ve yerel olarak test edilmesini ister. Geliştiriciler, bir yapı sunucusu kullanarak veya yerleşik Azure özelliklerini temel alarak sürekli tümleştirme (CI) ve/veya sürekli teslimi/dağıtımı (CD) yapılandırabilir.

CI/CD kullanarak bir ASP.NET Core uygulaması geliştirmeye başlamak için Azure DevOps Services veya kuruluşunuzun kendi Team Foundation Server (TFS) kullanabilirsiniz.

### <a name="initial-setup"></a>Başlangıç kurulumu

Uygulamanız için bir yayın işlem hattı oluşturmak için, uygulama kodunuzun kaynak denetiminde olması gerekir. Yerel bir depo ayarlayın ve bir takım projesindeki uzak depoya bağlayın. Aşağıdaki yönergeleri izleyin:

- [Kodunuzu git ve Visual Studio Ile paylaşma](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) veya

- [Kodunuzu TFVC ve Visual Studio ile paylaşma](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Uygulamanızı dağıtacağınız bir Azure App Service oluşturun. Azure portal uygulama hizmetleri dikey penceresine giderek bir Web uygulaması oluşturun. \+ Ekle ' ye tıklayın, Web uygulaması şablonunu seçin, Oluştur ' a tıklayın ve bir ad ve diğer ayrıntılar sağlayın. Web uygulamasına {Name}. azurewebsites. net adresinden erişilebilecektir.

![AzureWebApp](./media/image10-2.png)

**Şekil 10-1.** Azure portalında yeni bir Azure App Service Web uygulaması oluşturma.

CI derleme işleminiz, projenin kaynak denetimi deposuna yeni kod her işlendiği zaman otomatik bir derleme gerçekleştirir. Bu, kodun derlemelerine anında geri bildirim verir (ve ideal olarak otomatikleştirilmiş testler geçirir) ve potansiyel olarak dağıtılabilir. Bu CI derlemesi bir Web dağıtımı paketi yapıtı oluşturacak ve bunu CD işleminiz tarafından tüketimine yayımlayacak.

[CI derleme işleminizi tanımlama](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Takımınızın her biri yeni kod işlediğinde, sistemin bir derlemeyi sıraya alması için sürekli tümleştirmeyi etkinleştirdiğinizden emin olun. Derlemeyi test edin ve yapıtlarından biri olarak bir Web dağıtımı paketi üretdiğini doğrulayın.

Bir derleme başarılı olduğunda, CD işleminiz, CI derlemenize ait sonuçları Azure Web uygulamanıza dağıtacaktır. Bunu yapılandırmak için, Azure App Service dağıtım yapılacak bir *Sürüm*oluşturup yapılandırırsınız.

[CD yayın işleminizi tanımlama](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

CI/CD işlem hattınız yapılandırıldıktan sonra, Web uygulamanızda güncelleştirmeler yapmanız ve bunları dağıtmak için kaynak denetimine uygulamanız yeterlidir.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Azure 'da barındırılan ASP.NET Core uygulamaları geliştirmeye yönelik iş akışı

Azure hesabınızı ve CI/CD işleminizi yapılandırdıktan sonra, Azure 'da barındırılan ASP.NET Core uygulamaları geliştirme basittir. Aşağıda, Şekil 10-2 ' de gösterildiği gibi, Web uygulaması olarak Azure App Service barındırılan bir ASP.NET Core uygulaması oluştururken genellikle gereken temel adımlar verilmiştir.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Şekil 10-2.** ASP.NET Core uygulamalar oluşturmak ve bunları Azure 'da barındırmak için adım adım iş akışı

#### <a name="step-1-local-dev-environment-inner-loop"></a>1\. Adım. Yerel geliştirme ortamı iç döngüsü

ASP.NET Core uygulamanızı Azure 'a dağıtmak için geliştirme, aksi takdirde uygulamanızı geliştirmekten farklı değildir. Visual Studio 2017 veya DotNet CLı ile Visual Studio Code ya da tercih ettiğiniz düzenleyiciden bağımsız olarak, rahat bir şekilde sahip olduğunuz yerel geliştirme ortamını kullanın. Değişiklikleri paylaşılan kaynak denetimi deponuza göndermeye hazırlanana kadar, kod yazabilir, değişikliklerinizi çalıştırabilir ve hata ayıklamanıza, otomatikleştirilmiş testleri çalıştırmanıza ve kaynak denetimine yerel yürütmeler yapabilirsiniz.

#### <a name="step-2-application-code-repository"></a>2\. Adım Uygulama kodu deposu

Kodunuzu ekibinizle paylaşmaya her seferinde, değişikliklerinizi yerel kaynak deponuzdan takımınızın paylaşılan kaynak deposuna göndermeniz gerekir. Özel bir dalda çalışıyorsanız, bu adım genellikle kodunuzun paylaşılan bir dala birleştirilmesi (Belki de bir [çekme isteği](https://docs.microsoft.com/azure/devops/git/pull-requests)aracılığıyla) içerir.

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Adım 3: Yapı sunucusu: sürekli tümleştirme. derleme, test, paket

Paylaşılan uygulama kodu deposuna her yeni bir kayıt yapıldığında yapı sunucusunda yeni bir derleme tetiklenir. CI sürecinin bir parçası olarak, bu derleme uygulamayı tam olarak derleyip her şeyin beklendiği gibi çalıştığını doğrulamak için otomatikleştirilmiş testleri çalıştırmalıdır. CI işleminin nihai sonucu, dağıtıma hazırlanmak üzere Web uygulamasının paketlenmiş bir sürümü olmalıdır.

#### <a name="step-4-build-server-continuous-delivery"></a>4\. Adım. Yapı sunucusu: sürekli teslim

Derleme başarılı olduktan sonra, CD işlemi oluşturulan derleme yapıtlarını seçer. Bu, bir Web dağıtımı paketi içerir. Yapı sunucusu bu paketi yeni oluşturulan bir hizmet ile değiştirerek Azure App Service ' a dağıtır. Genellikle bu adım bir hazırlama ortamını hedefler, ancak bazı uygulamalar bir CD işlemi aracılığıyla doğrudan üretime dağıtılır.

#### <a name="step-5-azure-app-service-web-app"></a>5\. Adım. Azure App Service Web App

Dağıtıldıktan sonra, ASP.NET Core uygulama bir Azure App Service Web uygulaması bağlamında çalışır. Bu Web uygulaması, Azure portalı kullanılarak izlenebilir ve daha fazla yapılandırılabilir.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>6\. Adım. Üretim izleme ve tanılama

Web uygulaması çalışırken, uygulamanın durumunu izleyebilir ve tanılama ve Kullanıcı davranışı verilerini toplayabilirsiniz. Application Insights, Visual Studio 'Ya dahil edilmiştir ve ASP.NET uygulamaları için otomatik izleme sağlar. Kullanım, özel durumlar, istekler, performans ve Günlükler hakkında bilgi verebilir.

## <a name="references"></a>Başvurular

**ASP.NET Core uygulamanızı derleyin ve Azure 'a dağıtın**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Önceki](test-asp-net-core-mvc-apps.md)
>[İleri](azure-hosting-recommendations-for-asp-net-web-apps.md)
