---
title: "Azure için geliştirme işlemi"
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | Azure için geliştirme işlemi"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: e676c1225f7d11381808040cf101e897e0726ad4
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="development-process-for-azure"></a>Azure için geliştirme işlemi

> _"Bulut ile kişiler ve küçük işletmeler kendi parmakları ek ve anında kurulu kurumsal sınıf hizmetler ayarlayın."_  
> _-Roy Stephan_

 ## <a name="vision"></a>Görme

> *İyi tasarlanmış ASP .NET Core uygulamaları, Visual Studio veya CLI dotnet ve Visual Studio Code veya tercih ettiğiniz düzenleyiciyi kullanarak istediğiniz şekilde geliştirin.*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core uygulamaları için geliştirme ortamı

### <a name="development-tools-choices-ide-or-editor"></a>Geliştirme araçları seçenekleri: IDE veya Düzenleyicisi

Microsoft, tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi tercih olup olmadığını, ASP.NET Core uygulamaları geliştirirken kapsamdaki sahiptir.

**Visual Studio 2017.** Kullanıyorsanız, *Visual Studio 2017* , sahip olduğu sürece, ASP.NET Core uygulamaları oluşturabilirsiniz *.NET Core platformlar arası geliştirme* yüklü iş yükü. Şekil 10-1 Visual Studio 2017 Kurulumu iletişim kutusunda gerekli iş yükü gösterir.

![](./media/image10-1.png)

**Şekil 10-1.** .NET Core iş yükü Visual Studio 2017 yükleniyor.

[Visual Studio 2017 İndir](https://www.visualstudio.com/downloads/)

**Visual Studio Code ve dotnet CLI** (Mac, Linux ve Windows için platformlar arası araçları). Herhangi bir geliştirme dili destekleyen bir basit ve platformlar arası Düzenleyicisi tercih ederseniz, Microsoft Visual Studio Code ve CLI dotnet kullanabilirsiniz. Bu ürünler Geliştirici iş akışı kolaylaştırır basit ancak güçlü bir deneyim sağlar. Ayrıca, Visual Studio Code uzantıları için C destekler\# ve web geliştirme, IntelliSense ve düzenleyici içindeki kısayol görevlere sağlama.

[.NET Core SDK yükle](https://www.microsoft.com/net/download/core)

[Visual Studio Kodu'nu yükle](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure barındırılan ASP.NET Core uygulamaları için geliştirme iş akışı

Uygulama geliştirme yaşam döngüsü ve yerel olarak test etme tercih edilen dillerini kullanarak uygulama kodlama her geliştiricinin makineden başlatır. Geliştiriciler kendi tercih edilen kaynak denetim sistemi seçebilir ve sürekli tümleştirme (CI) ve/veya sürekli teslim/dağıtım (bir yapı sunucusu kullanarak CD) yapılandırabilir veya yerleşik Azure özelliklerini temel alarak.

CI/CD kullanarak bir ASP.NET Core uygulama geliştirme ile çalışmaya başlamak için Visual Studio Team Services veya kuruluşunuzun kullanabilirsiniz kendi Team Foundation Server (TFS).

### <a name="initial-setup"></a>İlk kurulumu

Uygulamanız için bir yayın işlem hattı oluşturmak için uygulama kodunuzun kaynak denetiminde olması gerekir. Bir yerel deposu ayarlama ve bir takım projesi uzak deponuza bağlayın. Bu yönergeleri izleyin:

-   [Kodunuzu paylaşımı Git ve Visual Studio](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) veya

-   [Kodunuzu TFVC'yi ve Visual Studio ile paylaşma](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

Bir Azure uygulama hizmeti uygulamanızı dağıtacağınız oluşturun. Azure Portal'da App Services dikey penceresine geri giderek bir Web uygulaması oluşturun. Tıklatın + Ekle, Web uygulaması şablonu seçin, Oluştur'u tıklatın ve bir ad ve diğer ayrıntıları sağlayın. Web uygulaması {adından} erişilebilir olacaktır. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Şekil 10-2.** Azure Portalı'nda yeni bir Azure App Service Web uygulaması oluşturma.

Yeni kod projenin kaynak denetimi deponuza kaydedilmiş olduğunda CI yapı işleminizin bir otomatik derleme gerçekleştirir. Bu kod derlemeler anında geri bildirim sağlar (ve, ideal olarak, otomatikleştirilmiş testleri geçirir) ve potansiyel olarak dağıtılabilir. Bu CI yapı web üretecektir paketi yapı dağıtmak ve CD işlem tarafından tüketim için yayımlayın.

[CI derleme işlemi tanımlayın](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

Birisi ekibinizin yeni kod uygulayan her sistemin bir yapıyı sıraya şekilde sürekli tümleştirme etkinleştirmeyi unutmayın. Yapı sınamak ve bir web oluşturan olduğunu doğrulayın paketini yapılarının biri olarak dağıtabilirsiniz.

Bir yapı başarılı olduğunda, CD işlemi, Azure web uygulamanızın CI yapınızın sonuçlarını dağıtın. Bu yapılandırma için oluşturun ve yapılandırın bir *sürüm*, Azure uygulama hizmetiniz dağıttığınız.

[CD yayın işlemi tanımlayın](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

CI/CD hattınızı yapılandırıldıktan sonra yalnızca web uygulamanız için güncelleştirmeler yapabilir ve bunları kaynak denetimine onlara dağıtılan uygulayın.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Azure barındırılan ASP.NET Core uygulamaları geliştirmek için iş akışı

Azure hesabınız ve CI/CD işleminizi yapılandırdıktan sonra Azure barındırılan ASP.NET Core uygulamaları geliştirme basit bir işlemdir. Şekil 10-3'te gösterildiği gibi Azure App Service'te bir Web uygulaması barındırılan bir ASP.NET Core uygulama oluştururken genellikle gerçekleştirmeniz temel adımlar verilmiştir.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Şekil 10-3.** ASP.NET Core uygulamaları oluşturma ve bunları Azure'da barındırmak için adım adım iş akışı

#### <a name="step-1-local-dev-environment-inner-loop"></a>Adım 1. Yerel geliştirme ortamı iç döngü

ASP.NET Core uygulamanızı azure'a geliştirme uygulamanızı aksi geliştirme farklı değildir. Visual Studio 2017 veya CLI dotnet ve Visual Studio Code veya tercih edilen düzenleyiciyi olup olmadığını kullanabileceğinizden, yerel geliştirme ortamı kullanın. Kod yazma, çalıştırın ve değişikliklerinizi hata ayıklama, otomatikleştirilmiş testleri çalıştırma ve paylaşılan kaynak denetimi deponuzun değişikliklerinizi gönderme hazırsınız kadar kaynak denetimine yerel işlemeleri olun.

#### <a name="step-2-application-code-repository"></a>Adım 2. Uygulama kodu deposu

Kodunuzu takımınızla paylaşmak için hazır olduğunda, ekibinizin paylaşılan kaynak deposu için yerel kaynak deposundan değişikliklerinizi gönderme. Özel bir şube çalışmakta, bu adım genellikle kodunuzu bir paylaşılan dala birleştirerek (belki de, bir [çekme isteği](https://www.visualstudio.com/docs/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Adım 3. Yapılandırma sunucusu: Sürekli tümleştirme. Derleme, Test, paketi

Paylaşılan uygulama kodu depoya yeni bir yürütme yapıldığında yeni bir yapı yapı sunucuda tetiklenir. CI işleminin bir parçası olarak, bu derleme tam olarak uygulama derlemek ve gerekir her şeyin beklendiği gibi çalıştığını doğrulamak için otomatikleştirilmiş testleri çalıştırma. CI işlemine ait sonuç paketlenmiş sürüm web uygulamasının, dağıtım için hazır olması gerekir.

#### <a name="step-4-build-server-continuous-delivery"></a>4. adım. Yapılandırma sunucusu: Kesintisiz teslim

Bir kez bir yapı başarılı olarak üretilen derleme yapıları CD işlemi seçer. Bu web içerecektir paketini dağıtabilirsiniz. Yapı sunucunun bu paket Azure App Service, herhangi bir varolan hizmeti ile yeni oluşturulan bir değiştirme dağıtır. Bu adımı hazırlama ortamında genellikle hedefler, ancak doğrudan bir CD işlemle üretim için bazı uygulamaları dağıtın.

#### <a name="step-5-azure-app-service-web-app"></a>5. adım. Azure uygulama hizmeti. Web uygulaması.

ASP.NET Core uygulama dağıtıldığında, Azure App Service Web uygulaması bağlamında çalışır. Bu Web uygulaması izlenebilir ve daha fazla Azure Portalı'nı kullanarak yapılandırılır.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>6. adım. Üretim izleme ve tanılama

Web uygulaması çalışırken, uygulama durumunu izlemenize ve tanılama ve kullanıcı davranış verileri toplayın. Application Insights, Visual Studio'da bulunan ve ASP.NET uygulamaları için otomatik araçları sunar. Bu, kullanım, özel durumlar, istekleri, performans ve Günlükler hakkında bilgi sağlayabilir.

## <a name="references"></a>Referanslar

**Derleme ve ASP.NET Core uygulamanızı Azure'a dağıtma**  
<https://www.VisualStudio.com/docs/Build/Apps/ASPNET/aspnetcore-to-Azure>


>[!div class="step-by-step"]
[Önceki] (test-asp-net-core-mvc-apps.md) [sonraki] (azure-hosting-recommendations-for-asp-net-web-apps.md)
