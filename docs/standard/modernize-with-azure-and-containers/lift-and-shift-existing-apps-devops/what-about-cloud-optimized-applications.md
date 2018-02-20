---
title: "Bulut için iyileştirilmiş uygulamaları nasıldır?"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bulut için iyileştirilmiş uygulamaları nasıldır?"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4cb85c9dbcc7586510db9947d0151e3856964ef4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="what-about-cloud-optimized-applications"></a>Bulut için iyileştirilmiş uygulamaları nasıldır?

Bulut iyileştirilmiş rağmen ve [bulut yerel](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) uygulamaları ana odak değildir bu kılavuz, bu modernization olgunluk seviyesi anlayışınız için ve bulut DevOps kullanıma hazır gelen ayırt etmek için yararlı olur.

Şekil 4-3 bulut iyileştirilmiş uygulamaları uygulama modernization olgunluk düzeylerinde yerleştirir:

![Bulut için iyileştirilmiş uygulamaları konumlandırma](./media/image3.png)

> **Şekil 4-3.** Bulut için iyileştirilmiş uygulamaları konumlandırma

Bulut için iyileştirilmiş modernization olgunluk seviyesi genellikle yeni geliştirme Yatırımlar gerektirir. Bulut için iyileştirilmiş düzeye genellikle taşıma maliyetleri azaltmak ve çeviklik artırmak mümkün olduğunca uygulamaları modernize iş gerek tarafından yönetilir ve rekabet avantajı. Bu hedefleri bulut PaaS kullanımını en üst düzeye çıkarma tarafından yapılır. Bu, yalnızca Azure uygulama hizmeti gibi platform işlem DBaaS, CaaS ve depolama hizmeti (STaaS) olarak aynı zamanda kendi uygulamaları ve Hizmetleri için bir PaaS geçirerek gibi PaaS Hizmetleri veya orchestrators kullanarak anlamına gelir.

Bu tür modernization yeniden düzenleme veya için optimize edilmiş yeni kod yazma genellikle gerektirir PaaS platformları (Azure App Service için benzer) bulut. Özellikle üzerinde mikro tabanlı bulut yerel uygulama modelleri için taşıyorsanız, özel bulut ortamı için mimariden bile gerektirebilir. Bu, bulut DevOps hiçbir mimarisinin yeniden düzenlenmesinden gerektiren hazır ve yeni kod karşılaştırıldığında faktörü ayrım bir anahtardır.

Daha gelişmiş bazı durumlarda, oluşturacağınız [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) tabanlı uygulamaları ile çeviklik gelişmesi ve ölçeklendirmek için tek yapılı bir mimaride elde etmek zor olurdu sınırları mikro mimarileri hakkında bir şirket içi ortamına dağıtılıyor.

Şekil 4-4 bulut iyileştirilmiş modeli kullandığınızda dağıtabileceğiniz uygulamaları türünü gösterir. İki temel seçenek modern web uygulamaları ve bulut-yerel uygulamaları var.

> ![Bulut için iyileştirilmiş düzeyinde uygulama türleri](./media/image4.png)
>
> **Şekil 4-4.** Bulut için iyileştirilmiş düzeyinde uygulama türleri

Yapay Intelligence (AI), machine learning (ML) ve IOT gibi diğer hizmetler ekleyerek temel modern web uygulamaları ve bulut-yerel uygulamalar genişletebilirsiniz. Olası bulut iyileştirilmiş yaklaşımlardan birini genişletmek için bu hizmetlerin herhangi birini kullanabilirsiniz.

Temel bulut iyileştirilmiş düzeyinde uygulamalarda uygulama mimarisinde farktır. [Bulut yerel](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) tanımı, üzerinde mikro tabanlı uygulamalar tarafından uygulamaları geçerlidir. Bulut yerel uygulamalar özel mimariler, teknolojiler ve platformlar, bir tek yapılı web uygulaması veya Geleneksel N katmanlı uygulama karşılaştırıldığında gerektirir.

Mikro kullanmayan yeni uygulamalar oluşturma mantığı vardır. Mikro tabanlı bir yaklaşım gereksinimlerinizi aşabilir birçok yeni ve hala modern senaryo vardır. Bazı durumlarda, yalnızca daha basit bir tek yapılı web uygulaması oluşturun ya da parçalı Hizmetleri N katmanlı uygulamayı eklemek isteyebilirsiniz. Bu durumda, Azure App Service tarafından sunulan olanlar gibi PaaS yetenekleri bulut tam kullanımı hala yapabilirsiniz. Bakım iş hala sınırla azaltın.

Ayrıca, yeni kodu geliştirmek için bulut iyileştirilmiş senaryolarda (tam bir uygulama veya kısmi alt sistemleri için), yeni kod oluşturduğunuzda, daha yeni sürümlerini .NET kullanması gereken ([.NET Core](https://docs.microsoft.com/dotnet/core/) ve [ASP.NET Core](https://docs.microsoft.com/aspnet/core/), özellikle). .NET Core yalın ve hızlı framework olduğundan mikro ve kapsayıcıları oluşturursanız, bu özellikle doğrudur. Küçük bellek kaplama alanı ve Hızlı Başlat kapsayıcılarında elde edersiniz ve uygulamalarınızı yüksek performanslı olacaktır. Bu yaklaşım mükemmel mikro ve kapsayıcıları gereksinimlerine en uygun ve bir platformlar arası framework-olma Linux, Windows Server ve Mac (Mac geliştirme ortamları için) aynı uygulamayı çalıştıramaz avantajları elde edin.

## <a name="cloud-native-applications-with-cloud-optimized-applications"></a>Bulut için iyileştirilmiş uygulamalarla bulut yerel uygulamalar

[Bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) büyük ve görev açısından kritik uygulamalar için daha gelişmiş veya olgun bir durumu. Bulut yerel uygulamalar genellikle yerine sıfırdan uygulamalara modernizing tarafından oluşturulan tasarımı ve mimarisini gerektirir. Bir bulut yerel uygulama ve PaaS için dağıtılan daha basit bir bulut için iyileştirilmiş web uygulaması arasındaki temel farklılık bulut yerel bir yaklaşım mikro mimarilerinde kullanmak için önerilir. Bulut iyileştirilmiş uygulamaları tek yapılı web uygulamaları veya PaaS hizmeti Azure uygulama hizmeti gibi bir buluta dağıtılan N katmanlı uygulamalar da olabilir.

[On iki öğeli uygulama](https://12factor.net/) (mikro yaklaşımları yakından ilişkilidir desenleri koleksiyonu) da bir gereksinimi dikkate [bulut yerel](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) uygulama mimarilerindeki.

[Bulut yerel bilgisayar Foundation (CNCF)](https://www.cncf.io/) birincil promoter bulut yerel ilkeler değil. Microsoft bir [CNCF üyesi](https://azure.microsoft.com/blog/announcing-cncf/).

Bir örnek tanımı ve bulut-yerel uygulamalar özellikleri hakkında daha fazla bilgi için Gartner makalesine bakın [mimari ve bulut-yerel uygulamalar tasarlamak nasıl](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Bir bulut yerel uygulama gerçekleştirme hakkında Microsoft'tan belirli yönergeler için bkz [.NET mikro: mimarisi kapsayıcılı .NET uygulamaları için](https://aka.ms/microservicesebook).

Tam bir uygulamaya geçirirseniz dikkate alınması gereken en önemli faktör [bulut yerel](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modeldir, mikro tabanlı bir mimari yeniden düzenlenmesine gerekir. Bu açıkça büyük yeniden düzenleme işlemi nedeniyle söz konusu geliştirme önemli yatırım gerektirir. Bu seçenek genellikle yeni düzeyde ölçeklenebilirlik ve uzun vadeli çeviklik gereken görev açısından kritik uygulamalar için seçilir. Ancak bulut-yerel doğru birkaç yeni senaryolar için mikro ekleyerek taşımadan ve sonuç olarak uygulamayı mikro tam olarak yeniden düzenlemeniz. Bu, bazı senaryolar için en iyi seçenektir artımlı bir yaklaşımdır.

## <a name="what-about-microservices"></a>Mikro nasıldır? 

Kuruluşunuz için bulut yerel uygulamalar değerlendirirken mikro ve nasıl çalıştığını anlamak önemlidir.

Mikro mimarisi, baştan veya mevcut uygulamaları gelişmesi oluşturulan uygulamaları için kullanabileceğiniz bir Gelişmiş yaklaşımdır (şirket içi veya Bulut DevOps kullanılmaya hazır uygulamalar) bulut yerel uygulamalar bulunun. Yeni mikro örneklerinde hakkında bilgi edinmek için var olan uygulamalar için birkaç mikro ekleyerek başlatabilirsiniz. Ancak Açıkçası, mimarı ve bu tür bir mimari yaklaşım özellikle için kod gerekir.

Ancak, mikro herhangi bir yeni ya da modern uygulama için zorunlu değildir. Mikro "Sihirli bullet" değildir ve her uygulama oluşturmak için tek, en iyi yolu değil. Nasıl ve ne zaman, kullandığınız mikro oluşturmak için gereken uygulama türüne bağlıdır.

Mikro mimarisi birden çok bağımsız alt sistemleri otonom Hizmetleri biçiminde dayalı dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen yaklaşım durumundadır. Mikro tabanlı bir mimari uygulamanın dağıtıldığı ve ölçeklendirilmiş bağımsız olarak geliştirilen, test edilmiş, sürümlü, olabilir hizmetler koleksiyonu yerleşik olarak bulunur. Bu, tüm ilgili, otonom veritabanı mikro hizmet başına içerebilir.

İndirilebilir PDF e-kitap, .NET Core kullanarak uygulayabileceğiniz bir mikro mimarisi ayrıntılı bir bakış için bkz: [.NET mikro: mimarisi kapsayıcılı .NET uygulamaları için](https://aka.ms/microservicesebook). Kılavuzu da kullanılabilir [çevrimiçi](https://docs.microsoft.com/dotnet/standard/microservices-architecture/).

Ancak, mikro hizmetler sunan güçlü özellikler bağımsız dağıtım, güçlü alt sınırlarını ve teknoloji seviyelerine senaryolarda bile-bunlar da birçok yeni zorluklar Yükselt. Sorunları, parçalanmış ve bağımsız veri modelleri gibi dağıtılmış uygulama geliştirme için ilişkili; mikro dayanıklı iletişimine elde; Nihai tutarlılık gereksinimini; ve işletim karmaşıklığını. Mikro karmaşıklık geleneksel tek yapılı uygulamalara kıyasla daha yüksek düzeyde tanıtır.

Mikro mimarisi karmaşıklığı nedeniyle, yalnızca belirli senaryolar ve belirli uygulama türleri mikro hizmet tabanlı uygulamalar için uygundur. Birden çok büyük ve karmaşık uygulamaları bunlar alt sistemleri gelişen. Bu durumlarda, bu artan uzun vadeli çeviklik ve daha verimli uygulama bakım için daha karmaşık bir yazılım mimarisinde yatırım değer olur. Ancak daha az karmaşık senaryolar için tek yapılı uygulama yaklaşımda devam etmek daha iyi olabilir veya basit N katmanlı yaklaşıyor.

Bu kavram hakkında yinelenen olma at the risk of bile son Not olarak uygulamalarınızda mikro kullanarak göz önünde bulundurmanız gerekir "all-in veya hiçbir şey tüm*.*" Genişletme ve yeni, üzerinde mikro göre küçük senaryoları ekleyerek varolan tek yapılı uygulamaları geliştirin. Sıfırdan bir mikro mimarisi yaklaşım ile çalışmaya başlamak için Başlat gerek yoktur. Aslında, yeni senaryolar ekleyerek varolan bir tek yapılı veya N katmanlı uygulama kullanarak gelişmesi öneririz. Sonuç olarak, otonom bileşenleri veya mikro uygulamasına aşağı bozulabilir. Tek yapılı uygulamalarınızı mikro yönde, adım adım gelişen başlatabilirsiniz.

## <a name="when-to-use-azure-app-service-for-modernizing-existing-net-apps"></a>Var olan .NET uygulamaları modernizing için Azure App Service'i kullanma zamanı

Web uygulamalarınızı .NET Framework kullanılarak geliştirilen çünkü bulut iyileştirilmiş olgunluk seviyesi için mevcut ASP.NET web uygulamaları modernize olduğunda, ana Windows ve büyük olasılıkla, Internet Information Server (IIS) bağımlılıklardır. Kullanın ve Windows ve IIS tabanlı uygulamaları dağıtmak için doğrudan dağıtarak ya da [Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is) ya da Windows kapsayıcıları kullanarak uygulamanız tarafından ilk containerizing. Containerizing, ya da dağıtırken Windows kapsayıcılara barındıran (VM tabanlı) veya bir Azure Service Fabric kümesi destekleyen Windows kapsayıcıları.

Windows kapsayıcıları kullandığınızda, verilerin kapsayıcıyla taşınmasını, tüm avantajlarını elde edersiniz. Sevkiyat ve uygulamanızı dağıtma çeviklik artırmak ve ortam konuları (hazırlama, geliştirme ve test, üretim) için uyuşmazlık azaltın. Sonraki birkaç bölümlerde, biz kapsayıcıları kullanarak elde edeceğiniz avantajlardan hakkında daha fazla ayrıntı uygulamasına gidin.

Bu kılavuz makalenin yazıldığı sırada Azure uygulama hizmeti Windows kapsayıcıları desteklemez. Linux için kapsayıcıları destekler. Sonraki Soru olabilir bunu, "Nasıl seçmem Windows kapsayıcıları ve Azure uygulama hizmeti arasında?"

Temel olarak, Azure App Service uygulamanız için çalışır ve herhangi bir sunucu veya uygulama hizmeti kullanılacak yol engelleme özel bağımlılıklar yok varolan .NET web uygulamanızı App Service'e geçirmeniz gerekir. Uygulamanızı korumak için kolay ve etkili şekilde olmasıdır. Azure'da, uygulamanızın de daha basit bir bakım yolu DBaaS, CaaS ve STaaS gibi PaaS altyapısından avantajları nedeniyle sahip olur.

Ancak, uygulamanızın sunucusu veya Azure App Service'te desteklenmeyen özel bağımlılıkları varsa, Windows kapsayıcılarında tabanlı seçenekleri dikkate almanız gerekebilir. Sunucu veya özel bağımlılıkları üçüncü taraf yazılım veya .msi dosyası, sunucuda yüklü olması gerekir, ancak, Azure App Service'te desteklenmeyen örneklerindendir. Azure App Service'te derlemeleri genel derleme önbelleği (GAC) veya COM kullanarak gibi desteklenmeyen herhangi bir sunucu yapılandırma başka bir örnektir / COM + bileşenleri. Windows kapsayıcı görüntülerini sayesinde aynı "birim dağıtımının.", özel bağımlılıkları içerebilir

Alternatif olarak, uygulamanızın Azure App Service tarafından desteklenmeyen alanlarını yeniden düzenlemeniz. İş birimi bağlı olarak yeniden düzenleme duyar, bunun değer olup olmadığını dikkatlice değerlendirin etmesi gerekir.

### <a name="benefits-of-moving-to-azure-app-service"></a>Azure App Service'e taşıma avantajları

Azure uygulama hizmeti teklifini tam yönetilen bir PaaS iş süreçlerini tarafından desteklenen web uygulamaları geliştirmek kolaylaştırır ' dir. Uygulama hizmeti kullandığınızda, web uygulamaları şirket içi Bakım ve yükseltme ile ilişkilendirilmiş altyapı yönetim maliyetlerini kaçının. Özellikle, donanım ve web uygulamaları şirket içi çalışan lisanslama maliyetleri keser.

Web uygulamanızı Azure App Service'e geçirilmesi için uygun değilse, ana avantajı, uygulama taşınması için gereken kısa sürede ' dir. Uygulama hizmeti kullanmaya başlamak çok kolay bir ortam sağlar.

Web uygulamalarının çalıştırılması için kullanabileceğiniz Azure içinde basit PaaS olduğundan azure uygulama hizmeti çoğu web uygulamaları için en iyi seçimdir. Dağıtım ve yönetim platformuyla doğrudan tümleşik, sitelerini hızlı bir şekilde yüksek trafik yükleri işlemesini ölçeklendirmek ve yerleşik Yük Dengeleme ve trafik Yöneticisi yüksek kullanılabilirlik sağlar.

Web uygulamalarınızı bile izleme Azure Application Insights ile basit bir işlemdir. Application Insights ücretsiz uygulama hizmeti ile gelir ve uygulamanızda herhangi bir özel kod yazmadan gerektirmez. Yalnızca App Service'te web uygulamanızı çalıştırmak ve ek bir iş ile ilgi çekici bir izleme sistemi elde edersiniz.

Uygulama hizmeti ile (örneğin, WordPress veya Umbraco) Azure Web uygulaması Galerisi'nden birçok açık kaynak uygulamaları doğrudan da kullanabilirsiniz veya framework ve ASP.NET gibi tercih ettiğiniz Araçları'nı kullanarak yeni bir site oluşturabilirsiniz. Uygulama hizmeti WebJobs özelliğini arka plan işi uygulama hizmeti web uygulamanızı işleme eklemek kolaylaştırır.

Web uygulamalarınızı Azure App Service Web Apps özelliğini kullanarak geçiş işleminin anahtar avantajları şunlardır:

-   Yoğun saatlerde talebi karşılamak ve sessiz saatlerde maliyetlerini azaltmak için otomatik ölçeklendirme.

-   Değişiklikleri ve verileri korumak üzere otomatik site yedeklemeler.

-   Yüksek kullanılabilirlik ve Azure PaaS platformunda esnekliği.

-   Dağıtım yuvaları birden çok site tasarımları test ve geliştirme ve hazırlık ortamları için.

-   Yük Dengeleme ve dağıtılmış hizmet engelleme (DDoS) koruma.

-   En yakın coğrafi dağıtım kullanıcıları yönlendirmek için trafik Yönetimi'ni kullanın.

Uygulama hizmeti yeni web uygulamaları için en iyi seçim olabilir, ancak yalnızca, uygulama bağımlılıkları App Service'te destekleniyorsa ancak var olan uygulamalar için uygulama hizmeti en iyi seçenek olabilir.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Azure App Service için Uyumluluk analizi**  
[https://www.migratetoazure.net/Resources](https://www.migratetoazure.net/Resources)


### <a name="benefits-of-moving-to-windows-containers"></a>Windows kapsayıcılara taşıma avantajları

Windows kapsayıcıları kullanmanın ana avantajı, kapsayıcılı olmayan uygulamalara kıyasla daha güvenilir ve geliştirilmiş dağıtım bir deneyim, elde ' dir. Ayrıca, uygulamanız ile kapsayıcıları etkili bir şekilde modernized uygulamanızı birçok diğer platformlar ve Windows kapsayıcıları destekler Bulutlar için hazır sağlar. Windows kapsayıcılara taşıma avantajlarını sonraki bölümlerde daha ayrıntılı olarak ele alınmaktadır.

Windows kapsayıcıları destekler, Azure'da (Orta 2017'dan sonra genel kullanılabilirlik) birincil işlem ortamlarda Azure Service Fabric ve temel Windows kapsayıcıları ana bilgisayar (Windows Server 2016 VM'ler)'dır. Bu ortamlar bu kılavuzda ele ana altyapı senaryolar verilmiştir.

Ayrıca, Windows kapsayıcıları Kubernetes, Docker Swarm veya DC/OS gibi diğer orchestrators dağıtabilirsiniz. Şu anda (önceden düşen 2017), bu Önizleme'de Azure kapsayıcı hizmeti Windows kapsayıcıları kullanma platformlarına.

>[!div class="step-by-step"]
[Önceki](microsoft-technologies-in-cloud-devops-ready-applications.md)
[sonraki](how-to-deploy-existing-net-apps-to-azure-app-service.md)
