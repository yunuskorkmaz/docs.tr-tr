---
title: ".NET Framework ile çalışmaya başlama"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66e581e04aa0c3d33fb1ef9a7f4163d131f625bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-the-net-framework"></a>.NET Framework ile çalışmaya başlama

.NET Framework hedefleyen .NET Framework uygulamaları yöneten bir çalışma zamanı yürütme ortamıdır. Bu bellek yönetimi ve diğer sistem hizmetleri ve sağlam yararlanmak programcıları sağlayan bir kapsamlı sınıf kitaplığı sağlayan ortak dil çalışma zamanını, uygulama geliştirme, tüm önemli alanlar için güvenilir kod oluşur.

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>.NET Framework nedir?

.NET Framework çeşitli hizmetlere çalışan kendi uygulamalarını sağlayan bir yönetilen yürütme ortamıdır. İki ana bileşenden oluşur: uygulamaları ve test kitaplığını sağlar, .NET Framework sınıf kitaplığı, çalışan işleme yürütme altyapısı, ortak dil çalışma zamanı (CLR), geliştiricilerin kendi uygulamalardan çağırabilirsiniz yeniden kullanılabilir kod. Çalışan uygulamalar için .NET Framework sağladığı hizmetler şunlardır:

- Bellek yönetimi. Birçok programlama dilindeki programcıları ayırma ve belleği serbest bırakma ve nesne yaşam süresi işleme için sorumludur. .NET Framework uygulamalarında CLR uygulama adına bu hizmetleri sağlar.

- Ortak tür sistemi. Geleneksel programlama dillerinde temel türleri diller arası birlikte çalışabilirlik karmaşıklaştırır derleyici tarafından tanımlanır. .NET Framework'te temel türleri .NET Framework türü sistem tarafından tanımlanır ve .NET Framework hedefleyen tüm diller için ortak olan.

- Bir kapsamlı sınıf kitaplığı. Çok büyük miktarda ortak alt düzey programlama işlemleri işlemek için kod yazmaya gerek yerine programcıları .NET Framework Sınıf Kitaplığı ' türleri ve üyeleri erişilmeye kitaplığını kullanın.

- Geliştirme çerçeveleri ve teknolojiler. .NET Framework için ASP.NET web uygulamaları için veri erişimi için ADO.NET ve Windows Communication Foundation Hizmet odaklı uygulamalar için uygulama geliştirme belirli alanlarında kitaplıklarını içerir.

- Diller arası birlikte çalışabilirlik. .NET Framework hedefleyen dil derleyicileri ortak Ara dili (hangi sırayla, ortak dil çalışma zamanı tarafından çalışma zamanında derlenen CIL), adlandırılmış bir ara kod yayma. Bu özellik ile bir dilde yordamları diğer dillere ve bunların tercih edilen dillerde uygulamalar oluşturma programcıları odak erişilebilir.

- Sürüm uyumluluğu. Nadir istisnalar belirli bir .NET Framework sürümü kullanılarak geliştirilen uygulamaları değişiklik yapmadan sonraki bir sürümünü çalıştırın.

- Yan yana yürütme. .NET Framework sürüm çakışmaları birden çok sürümü aynı bilgisayarda mevcut için ortak dil çalışma zamanı sağlayarak yardımcı olur. Bunun anlamı uygulamaların birden fazla sürümleri bulunabilir ve bir uygulama ile oluşturulan .NET Framework sürümünde çalıştırabilirsiniz. Yan yana yürütme, .NET Framework sürümü gruplarını 1.0/1.1, 2.0/3.0/3.5 ve 4/4.5.x/4.6.x/4.7.x için geçerlidir.

- Çoklu sürüm desteği. Hedefleyerek [.NET standart](~/docs/standard/net-standard.md), geliştiriciler Windows 7, Windows 8, Windows 8.1, Windows 10, Windows Phone ve Xbox 360 gibi birden çok .NET Framework platformlarında çalışan derlemeler oluşturun.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Kullanıcılar için .NET Framework

.NET Framework uygulamalarını geliştirmek yoktur, ancak bunları kullanmak, .NET Framework veya çalışması hakkındaki belirli bilgileri sağlamak için gerekli değil. Çoğunlukla, .NET Framework kullanıcılara tamamen saydamdır.

Windows işletim sistemi kullanıyorsanız, .NET Framework zaten bilgisayarınızda yüklü olabilir. Ayrıca, .NET Framework gerektiren bir uygulama yüklerseniz, uygulamanın Kurulum programının bilgisayarınızda belirli bir .NET Framework sürümünü yükleyebilirsiniz. Bazı durumlarda, .NET Framework'ü yüklemek için soran bir iletişim kutusu görebilirsiniz. Bu iletişim kutusu görüntülendiğinde ve bilgisayarınızda Internet erişimi varsa, bir uygulamayı çalıştırmak yalnızca çalıştınız varsa, .NET Framework'ün eksik sürümünü yüklemenize olanak tanıyan bir Web sayfasına gidebilirsiniz.

Genel olarak, bilgisayarınızda yüklü .NET Framework sürümlerini kaldırmanız gerekir. Bu iki nedeni vardır:

- Belirli bir .NET Framework sürümünü kullandığınız uygulama bağımlı olması durumunda, bu uygulama bu sürümü kaldırılırsa kesilebilir.

- .NET Framework'ün bazı sürümlerinde, önceki sürümlerin yerinde güncelleştirmelerdir. Örneğin, [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] sürüm 2.0 bir yerinde güncelleştirmesidir ve 4.7.1 .NET Framework sürüm 4, 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2 ve 4.7 için bir yerinde güncelleştirmesidir. Daha fazla bilgi için bkz: [.NET Framework sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md).

.NET Framework'ü seçerseniz, her zaman kullanmanız **programlar ve Özellikler** kaldırmak için Denetim Masası'ndan. Hiçbir zaman, .NET Framework sürümünü el ile kaldırın.

.NET Framework'ün birden çok sürümü aynı anda tek bir bilgisayarda bulunabilir unutmayın. Başka bir deyişle, sonraki bir sürümünü yüklemek için önceki sürümlerini kaldırmanız gerekmez.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>Geliştiriciler için .NET Framework

Bir geliştirici değilseniz, uygulamalarınızı oluşturmak için .NET Framework'ü destekleyen herhangi bir programlama dili seçin. .NET Framework dil bağımsızlığı ve birlikte çalışabilirlik sağladığından, diğer .NET Framework uygulamaları ve bileşenleri ile bunların geliştirilen dil bakılmaksızın ile etkileşim.

.NET Framework uygulamaları veya bileşenleri geliştirmek için aşağıdakileri yapın:

1. İşletim sisteminizde önceden değil, uygulamanızı hedeflediğini .NET Framework sürümünü yükleyin. En son ürün sürümü .NET Windows 10 sonbaharda oluşturucuları Update'te önceden yüklenmiş ve Windows işletim sisteminin önceki sürümlerinde indirilebilir 4.7.1, altyapısıdır. .NET Framework sistem gereksinimleri için bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md). Diğer .NET Framework sürümlerini yükleme hakkında daha fazla bilgi için bkz: [Yükleme Kılavuzu](../../../docs/framework/install/guide-for-developers.md). Ek .NET Framework paketler herhangi normal veya zamanlanmış yayın döngüsü dışında çalışırken temelinde kullanıma, yani bant dışı bırakılır. Bu paketleri hakkında daha fazla bilgi için bkz: [.NET Framework ve bant dışı sürümler](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).

2. Dil veya uygulamalarınızı geliştirmek için kullanmak istediğiniz .NET Framework tarafından desteklenen dilleri seçin. Çok sayıda dilde Visual Basic, C#, Visual F # ve C + dahil olmak üzere, kullanılabilir +/ CLI Microsoft'tan. (.NET Framework aynılarını için uygulamalar geliştirmenize olanak tanıyan bir programlama dili [ortak dil altyapısı (CLI) belirtimi](http://go.microsoft.com/fwlink/?LinkId=199862).)

3. Seçin ve geliştirme yükleyin ve, uygulamalarınızı oluşturmak için kullanılacak ortamı seçili programlama dili veya dilleri destekler. .NET Framework uygulamaları için Microsoft tümleşik geliştirme ortamı (IDE) [Visual Studio](http://go.microsoft.com/fwlink/?LinkId=325532). Sürümleri bir süre içinde kullanılabilir.

.NET Framework hedefleyen uygulamaları geliştirme hakkında daha fazla bilgi için bkz: [geliştirme Kılavuzu](../../../docs/framework/development-guide.md).

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| ----- |------------ |
| [Genel bakış](../../../docs/framework/get-started/overview.md) | .NET Framework hedefleyen uygulamalar oluşturan geliştiriciler için ayrıntılı bilgiler sağlar. |
| [Yükleme Kılavuzu](../../../docs/framework/install/index.md) | .NET Framework yükleme hakkında bilgi sağlar. |  
| [.NET Framework ve bant dışı yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md) | Bandı serbest bırakır ve bunları uygulamanızda nasıl kullanacağınızı dışında .NET Framework'ü açıklar. |
| [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md) | .NET Framework çalıştırmak için gereken donanım ve yazılım gereksinimleri listelenmiştir. |
| [.NET core ve açık kaynak](../../../docs/framework/get-started/net-core-and-open-source.md) | .NET Framework ve açık kaynaklı .NET Core projelere erişmek nasıl bağlantılı olarak .NET Core açıklar. |
| [.NET core belgeleri](https://docs.microsoft.com/dotnet/) | Kavramsal sağlar ve .NET Core API başvuru belgeleri. |

## <a name="see-also"></a>Ayrıca bkz.

[.NET framework Kılavuzu](../../../docs/framework/index.md)   
[Yenilikler](../../../docs/framework/whats-new/index.md)   
[.NET API tarayıcı](/dotnet/api/)   
[Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
