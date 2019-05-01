---
title: Azure için geliştirme işlemi
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Azure için geliştirme işlemi
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: b7a6ae343feae7c28fb7debdc8a6b617872d262f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019399"
---
# <a name="development-process-for-azure"></a>Azure için geliştirme işlemi

> _"Bulut sayesinde, kişilerin ve küçük ölçekli işletmeler kendi parmağınızı Yasla ve anında kurumsal sınıf Hizmetleri'ni ayarlama."_  
> _-Roy Stephan_

## <a name="vision"></a>Vision

> *İyi tasarlanmış ASP .NET Core uygulamaları Visual Studio veya dotnet CLI ve Visual Studio Code veya tercih ettiğiniz düzenleyiciyi kullanarak dilediğiniz şekilde geliştirin.*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core uygulamaları için geliştirme ortamı

### <a name="development-tools-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da basit ve Çevik bir düzenleyici tercih olsun, Microsoft ASP.NET Core uygulamaları geliştirirken, işinize yarayacaktır.

**Visual Studio 2017.** Kullanıyorsanız *Visual Studio 2017* sahip olduğunuz sürece, ASP.NET Core uygulamaları oluşturabilirsiniz *.NET Core çoklu platform geliştirme* iş yükü yüklenmiş. Şekil 10-1, Visual Studio 2017 Kurulum iletişim kutusunda gerekli iş yükü gösterir.

![](./media/image10-1.png)

**Şekil 10-1.** Visual Studio 2017'de .NET Core iş yükü yükleniyor.

[Visual Studio 2017 İndir](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code ve CLI dotnet** (Mac, Linux ve Windows için platformlar arası araçları). Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyici tercih ederseniz, Microsoft Visual Studio Code ve CLI dotnet kullanabilirsiniz. Bu ürünler, geliştirici iş akışını kolaylaştıran bir basit ama güçlü bir deneyim sağlar. Ayrıca, Visual Studio Code için C uzantıları destekler\# ve web geliştirme, IntelliSense ve düzenleyici içindeki kısayol görevleri sağlar.

[.NET Core SDK'sını indirin](https://www.microsoft.com/net/download/core)

[Visual Studio Code'u indirin](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure'da barındırılan ASP.NET Core uygulamaları için geliştirme iş akışı

Kendi tercih edilen dili ve yerel olarak test uygulama kodlama her geliştiricinin makinesinden uygulama geliştirme yaşam döngüsünü başlatır. Geliştiriciler kendi tercih edilen kaynak denetim sistemi seçebilir ve sürekli tümleştirme (CI) ve/veya sürekli teslim/dağıtım (bir yapı sunucusunu kullanarak CD) yapılandırabilirsiniz veya yerleşik Azure özelliklerini temel alarak.

CI/CD kullanarak bir ASP.NET Core uygulaması geliştirme ile çalışmaya başlamak için Azure DevOps Services veya kuruluşunuzun kullanabilirsiniz kendi Team Foundation Server (TFS).

### <a name="initial-setup"></a>Başlangıç kurulumu

Uygulamanız için bir yayın işlem hattı oluşturmak için uygulama kodunuzun kaynak denetiminde olması gerekir. Yerel depo ayarlama ve bir takım projesindeki uzak deponuza bağlayın. Bu yönergeleri izleyin:

- [Git ve Visual Studio ile kodunuzu paylaşmaya](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) veya

- [TFVC ve Visual Studio ile kodunuzu paylaşın](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Bir Azure App Service uygulamanızı dağıtacağınız oluşturun. Azure portalında uygulama hizmetleri dikey penceresine giderek bir Web uygulaması oluşturun. Tıklama + Ekle, Web uygulaması şablonu seçin, Oluştur'a tıklayın ve bir ad ve diğer ayrıntıları sağlayın. Web uygulaması ' {name} önbelleğinden erişilemez. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Şekil 10-2.** Azure Portalı'nda yeni bir Azure App Service Web uygulaması oluşturma.

Yeni kod projenin kaynak denetimi deponuza taahhüt olduğunda CI yapı işleminizin otomatik bir yapı gerçekleştirir. Bu kod derlenir anında geri bildirim sağlar (ve, ideal olarak, otomatik testler geçer) ve potansiyel olarak dağıtılabilir. Bu bir CI yapısı web üretecektir paket yapıt dağıtma ve CD işleminiz tarafından tüketim için yayımlayın.

[CI yapı işleminizi tanımlama](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Takımınızdaki birinin yeni bir kod tarafından işlenen her sistemin bir yapıyı sıraya için sürekli tümleştirmeyi etkinleştirmek emin olun. Derleme test ve web üretme olduğunu doğrulayın. paket yapıtlarını biri olarak dağıtın.

Bir derleme başarılı olduğunda, CD işlemiyle CI yapı sonuçlarını, Azure web uygulamanıza dağıtın. Bunu yapılandırmak için oluşturma ve yapılandırma bir *yayın*, Azure App Service'e dağıtacağınız.

[CD sürüm işleminizi tanımlama](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

CI/CD ardışık düzeninizi yapılandırıldıktan sonra basitçe web uygulamanızı güncelleştirme yapmak ve bunları dağıtılan için kaynak denetimine işleyin.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Azure'da barındırılan ASP.NET Core uygulamaları geliştirmek için iş akışı

Azure hesabınızı ve CI/CD işleminizi yapılandırdıktan sonra Azure'da barındırılan ASP.NET Core uygulamaları geliştirme basittir. Şekil 10-3'te gösterildiği gibi Azure App Service'te bir Web uygulaması barındırılan bir ASP.NET Core uygulaması derlerken, genellikle uygulayacağınız temel adımlar verilmiştir.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Şekil 10-3.** ASP.NET Core uygulamaları oluşturmak ve bunları Azure'da barındırmak için adım adım iş akışı

#### <a name="step-1-local-dev-environment-inner-loop"></a>Adım 1. Yerel geliştirme ortamı iç döngü

ASP.NET Core uygulamanızı azure'a geliştirme, aksi halde uygulamanızı geliştirme farklı değildir. Visual Studio 2017 veya dotnet CLI ve Visual Studio Code veya tercih ettiğiniz düzenleyiciyi olup olmadığını, yararlanacağınız yerel geliştirme ortamı kullanın. Kod yazın, çalıştırın ve değişikliklerinizi hata ayıklama, otomatik testleri çalıştırmak ve değişiklikleri paylaşılan kaynak denetim deponuza göndermeye hazır oluncaya kadar kaynak denetimi yerel işlemeleri olun.

#### <a name="step-2-application-code-repository"></a>Adım 2. Uygulama kod deposu

Kodunuzu takımınızla paylaşmak hazır olduğunda, takımınızın paylaşılan kaynak deposu için yerel kaynak deponuzdan değişikliklerinizi gönderme. Özel bir dalda aşinaysanız, bu adım genellikle kodunuzu paylaşılan bir dalla birleştirilmesini içerir (belki de, bir [çekme isteği](https://docs.microsoft.com/azure/devops/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Adım 3. Yapı sunucusu: Sürekli Tümleştirme. derleme, test paketi

Yeni bir yapı, yapı sunucusunda paylaşılan uygulama kodu deposunun yeni bir işleme yapıldığında tetiklenir. CI işleminin bir parçası olarak, bu derleme tam olarak uygulamayı derleyin ve her şeyin beklendiği şekilde çalıştığını doğrulamak için otomatik testler çalıştırın. CI işlem son sonucunu dağıtıma hazır web uygulaması paketlenmiş bir sürümü olmalıdır.

#### <a name="step-4-build-server-continuous-delivery"></a>4. adımı. Yapı sunucusu: Sürekli teslim

Bir derleme başarılı olana sonra CD işlemiyle üretilen derleme yapıları seçer. Bu web içerecektir paketini dağıtabilirsiniz. Yapı sunucusunda bu paketin Azure App Service, yeni oluşturulan bir var olan herhangi bir hizmeti değiştirerek dağıtır. Bu adım bir hazırlık ortamı genellikle hedefler, ancak bazı uygulamaları doğrudan bir CD işlemiyle üretime dağıtın.

#### <a name="step-5-azure-app-service-web-app"></a>5. adımı. Azure App Service Web uygulaması

Dağıtıldıktan sonra ASP.NET Core uygulaması Azure App Service Web uygulaması bağlamında çalışır. Bu Web uygulaması izlenebilir ve Azure portalını kullanarak daha fazla yapılandırılmış.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>6. adım. Üretim izleme ve tanılama

Web uygulamasını çalışırken, uygulama durumunu izleyin ve tanılama ve kullanıcı davranış verileri toplayın. Application Insights, Visual Studio'ya eklenmiştir ve ASP.NET uygulamaları için otomatik izleme sunar. Bu, kullanım, özel durumlar, istekler, performans ve günlükleri hakkında daha fazla bilgi sağlayabilir.

## <a name="references"></a>Referanslar

**Derleme ve ASP.NET Core uygulamanızı Azure'a dağıtma**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Önceki](test-asp-net-core-mvc-apps.md)
>[İleri](azure-hosting-recommendations-for-asp-net-web-apps.md)