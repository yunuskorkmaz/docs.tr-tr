---
title: Bulutta çalışan uygulamalar hakkında neler diyeceksiniz?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Bulutta çalışan uygulamalar hakkında neler diyeceksiniz?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 10f7761b7c0d2ddd8cb9247b1a02aa49cdc4e5d4
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679287"
---
# <a name="what-about-cloud-native-applications"></a>Bulutta çalışan uygulamalar hakkında neler diyeceksiniz?

Ancak [bulutta yerel](https://azure.microsoft.com/overview/cloudnative/) uygulamaları odaklandığı değildir bu kılavuz, bu modernizasyonu olgunluk seviyesi bir anlayışa sahip ve bu bulut için iyileştirilmiş uygulamalardan ayırt etmek için yararlı olur.

Şekil 4-3, bulutta çalışan uygulamalar uygulama modernizasyonu olgunluk düzeyinde yerleştirir:

![Bulutta çalışan uygulamalar konumlandırma](./media/image3.png)

> **Şekil 4-3.** Bulutta çalışan uygulamalar konumlandırma

Bulutta yerel modernizasyonu olgunluk seviyesi, genellikle yeni geliştirme yatırımlarından gerektirir. Genellikle bulut yerel düzeye taşıma önemli ölçüde dağıtılabilir otonom alt (mikro) oluşturarak büyük uygulamalar ölçek ve ölçeği artırmak mümkün olduğunca uygulamaları modernize etme işletme ihtiyaçlarına göre bağımsız olarak yönetilir uzun dönem ve artışı evrimi çevikliği sağlayan bu otonom uygulamanın bölümlerinin maliyetlerini düşürürken çalışırken uygulamanın diğer bölgelerden avantajları önemli rekabet.

Bulutta çalışan uygulamalar, ana yapı taşına çeviklikle evrim geçiren ve şirket içi veya Bulut için Dağıtılmış bir tek parçalı mimari sağlamak zor olurdu limitleri ölçek, mikro hizmetler mimari yaklaşımları dayanır ortam.

Şekil 4-4, yerel bulut modelinin temel özellikleri gösterilmektedir.

> ![Buluta özgü özellikleri, mikro hizmetler, kapsayıcılar, bulut esnek, Düzenleyicileri sahiptir ve sunucusuz](./media/image4.png)
>
> **Şekil 4-4.** Buluta özgü özellikleri

Ayrıca, yapay zeka (AI), machine learning (ML) ve IOT gibi diğer hizmetler ekleyerek temel modern web uygulamaları ve bulutta çalışan uygulamaları genişletebilirsiniz. Olası bulut için iyileştirilmiş yaklaşımlardan birini genişletmek için bu hizmetlerin herhangi birini kullanabilirsiniz.

Bulutta yerel düzeyinde uygulamalarda temel fark uygulama mimaridir. Bulutta yerel uygulamalar üzerinde mikro hizmet tabanlı uygulamaları tanımına göre yapılandırılır. Bulutta yerel uygulamaların özel mimariler, teknolojiler ve platformlar, tek parçalı bir web uygulaması ya da geleneksel N katmanlı uygulama karşılaştırma gerektirir.

## <a name="cloud-native-applications-details"></a>Bulutta çalışan uygulamalar ayrıntıları

Bulutta yerel, büyük ve görev açısından kritik uygulamalar için daha gelişmiş veya olgun bir durumdur. Bulutta yerel uygulamalar genellikle mimarisi ve mevcut uygulamaları modernize etme tarafından oluşturulan yerine sıfırdan tasarım gerektirir. Bulutta çalışan uygulama ve daha basit bir bulut için iyileştirilmiş web uygulaması arasındaki temel fark, mikro hizmet mimarilerinde bulutta yerel bir yaklaşım kullanmak için önerilir. Bulut için iyileştirilmiş uygulamalar ayrıca monolitik web uygulamaları veya N katmanlı uygulamalar olabilir.

[On iki Faktörlü uygulama](https://12factor.net/) (mikro hizmetler yaklaşımları yakından ilgili düzenleri koleksiyonu) de bulutta yerel uygulama mimarileri için bir gereksinim olarak kabul edilir.

[Bulut yerel bilgisayar Foundation (CNCF)](https://www.cncf.io/) olan bir birincil promoter bulutta yerel ilkeler. Microsoft, bir [CNCF üyesi](https://azure.microsoft.com/blog/announcing-cncf/).

Örnek bir tanım ve bulutta çalışan uygulamalar özellikleri hakkında daha fazla bilgi için Gartner bkz [Mimar ve bulutta çalışan uygulamalar tasarlamak nasıl](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Bulutta çalışan bir uygulamanın nasıl uygulanacağını hakkında Microsoft'tan belirli yönergeler için bkz [.NET mikro Hizmetleri: Kapsayıcılı .NET uygulamaları mimarisi](https://aka.ms/microservicesebook).

Bir mikro hizmet tabanlı mimariye yeniden oluşturma, tam bir uygulama bulutta yerel modeline geçirme, dikkate alınması gereken en önemli faktör olan. Bu açıkça büyük yeniden düzenleme işlemi nedeniyle ilgili geliştirme önemli bir yatırım gerektirir. Bu seçenek, genellikle yeni düzeyde ölçeklenebilirlik ve uzun vadeli çevikliği gereken görev açısından kritik uygulamalar için seçilir. Ancak, doğru buluta özgü birkaç yeni senaryolar için mikro hizmetler ekleyerek taşımadan ve sonunda uygulamayı mikro Hizmetleri tam olarak yeniden düzenleme. Bazı senaryolar için en iyi seçenektir artımlı bir yaklaşımdır.

## <a name="what-about-microservices"></a>Mikro hizmetler hakkında neler diyeceksiniz?

Kuruluşunuz için bulutta çalışan uygulamalar değerlendirirken, mikro hizmetler ve nasıl çalıştığını anlamak önemlidir.

Mikro hizmet mimarisi, sıfırdan veya mevcut uygulamaları bulutta yerel uygulamaların doğru evrim Geçiren oluşturulan uygulamalar için kullanabileceğiniz Gelişmiş bir yaklaşımdır. Yeni mikro hizmetler paradigmalarını hakkında bilgi edinmek için mevcut uygulamaları birkaç mikro hizmetler ekleyerek başlayabilirsiniz. Ancak NET bir şekilde, Mimar ve kod, bu tür bir mimari yaklaşım özellikle de gerekir.

Ancak, mikro hizmetler, herhangi bir yeni ya da modern uygulama için zorunlu değildir. Mikro Hizmetler "Sihirli bullet" değildir ve bunlar her bir uygulama oluşturmak için tek ve en iyi yöntem değildir. Nasıl ve ne zaman, kullandığınız mikro hizmetler oluşturmak için ihtiyacınız olan uygulamanın türüne bağlıdır.

Mikro hizmet mimarisi, birden çok bağımsız alt sistemlerin otonom bir hizmetler biçiminde temel alan dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen yaklaşım gelmektedir. Bir mikro hizmet tabanlı mimari, uygulamaya dağıtılan ve ölçeği birbirinden bağımsız olarak geliştirilen, test edilmiş, tutulan, olabilir hizmetler koleksiyonu oluşturulmuştur. Bu, herhangi bir ilgili, otonom veritabanı mikro hizmet başına içerebilir.

İndirilebilir PDF e-kitap, .NET Core kullanarak uygulayabileceğiniz bir mikro hizmet mimarisi ayrıntılı bilgi için bkz [.NET mikro Hizmetleri: Kapsayıcılı .NET uygulamaları mimarisi](https://aka.ms/microservicesebook). Kılavuzu da kullanılabilir [çevrimiçi](../../microservices-architecture/index.md).

Ancak, mikro hizmetler sunan güçlü özellikleri bağımsız dağıtımı, sağlam alt sınırlarını ve teknoloji seviyelerine senaryolarda bile-bunlar birçok yeni zorluklar da Yükselt. Parçalanmış ve bağımsız veri modelleri gibi dağıtılmış uygulama geliştirme zorlukları ilgili; mikro hizmetler dayanıklı iletişimine elde; Son tutarlılık gereksinimini; ve işletimsel karmaşıklığın. Mikro hizmetler, geleneksel tek parçalı uygulamalarla karşılaştırıldığında karmaşıklığı yüksek seviyede tanıtır.

Bir mikro hizmet mimarisi karmaşıklığı nedeniyle, yalnızca belirli senaryolar ve belirli uygulama türlerini mikro hizmet tabanlı uygulamalar için uygundur. Birden çok büyük ve karmaşık uygulamaları bunlar alt sistemlerin gelişen. Bu gibi durumlarda, artan uzun vadeli çevikliği ve daha verimli uygulama bakımı için daha karmaşık bir yazılım mimarisindeki harcanmalıdır. Ancak daha az karmaşık senaryolar için bir parçalı uygulama yaklaşım ile devam etmek daha iyi olabilir veya basit N katmanlı yaklaşıyor.

Yinelenen bu kavramı hakkında edilerek at the risk of bile son Not olarak mikro hizmetler kullanarak uygulamalarınızda "tamamen veya hiçbir şey tüm." olarak göz önünde bulundurmanız olmamalıdır Genişletme ve var olan tek parçalı uygulamalarla yeni, üzerinde mikro hizmet tabanlı küçük senaryoları evrim Geçiren. Bir mikro hizmetler mimari yaklaşım ile çalışmaya başlamak için sıfırdan başlayın gerek yoktur. Aslında, yeni senaryolar ekleyerek mevcut tek parça veya N-katmanlı uygulamaya kullanarak gelişmek öneririz. Sonuç olarak, otonom bileşenler veya mikro hizmetler halinde uygulamayı bozabilir. Tek parça bir mikro hizmetler yönü, adım adım uygulamalarınızda gelişen başlayabilirsiniz.

Herhangi bir durumda, bu kılavuz temel olarak tek parça veya N katmanlı mimariler genellikle olan mevcut uygulamaları modernleştirme hedeflediği olduğundan mevcut bu kılavuzda kalan tüm "mikro hizmet tabanlı uygulama" çoğunu odaklanır.

> [!div class="step-by-step"]
> [Önceki](microsoft-technologies-in-cloud-optimized-applications.md)
> [İleri](deploy-existing-net-apps-as-windows-containers.md)
