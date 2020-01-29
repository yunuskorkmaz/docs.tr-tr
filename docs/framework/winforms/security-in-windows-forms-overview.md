---
title: Güvenliğe genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 9010b45383f856079661359fdf82180526d96dde
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734849"
---
# <a name="security-in-windows-forms-overview"></a>Windows Forms'ta Güvenliğe Genel Bakış

.NET Framework yayınlanmadan önce, bir kullanıcının bilgisayarında çalışan tüm kod, bilgisayarın bir kullanıcısının sahip olduğu kaynaklara erişmek için aynı haklara veya izinlere sahip. Örneğin, kullanıcının dosya sistemine erişmesine izin verildiyse, kodun dosya sistemine erişmesine izin verilir; kullanıcının bir veritabanına erişmesine izin verildiyse kodun bu veritabanına erişmesine izin verilir. Bu haklar veya izinler, kullanıcının yerel bilgisayarda açıkça yüklediği yürütülebilir dosyalarda kod için kabul edilebilir olsa da, Internet 'ten veya yerel Intranetten gelen kötü amaçlı olabilecek kod için kabul edilebilir olmayabilir. Bu kod, izin olmadan kullanıcının bilgisayar kaynaklarına erişememelidir.

.NET Framework, bu kodun, kullanıcının sahip olduğu haklara ait izinleri veya hakları ayırt etmenizi sağlayan kod erişim güvenliği adlı bir altyapı sunar. Varsayılan olarak, Internet 'ten ve Intranetten gelen kod yalnızca kısmi güven olarak bilinerek çalışabilir. Kısmi güven bir uygulamayı bir dizi kısıtlamayla tartışmalıdır: diğer şeyler arasında, bir uygulamanın yerel sabit diske erişimi kısıtlanmıştır ve yönetilmeyen kod çalıştırılamaz. .NET Framework, kodun kimliğine göre erişim izni verilen kaynakları denetler: nereden geldiği, [güçlü adlandırılmış derlemeler](../../standard/assembly/strong-named.md)içerip içermediğini ve bir sertifikayla imzalanıp imzalanmadığını ve bu şekilde devam eder.

Windows Forms uygulamalarını dağıtmak için kullandığınız ClickOnce teknolojisi, kısmi güvende, tam güvende veya yükseltilmiş izinlerle kısmi güvende çalışan uygulamalar geliştirmenizi kolaylaştırır. ClickOnce, uygulamanızın yerel kullanıcıdan sorumlu bir şekilde tam güven veya yükseltilmiş izinler isteyebilmesi için Izin yükseltme ve güvenilir uygulama dağıtımı gibi özellikler sağlar.

## <a name="understanding-security-in-the-net-framework"></a>.NET Framework güvenliği anlama

Kod erişimi güvenliği, kodun kaynaklandığı ve kodun kimliğinin diğer yönlerine bağlı olarak kodun farklı derecelerde güvenilmesini sağlar. Ortak dil çalışma zamanının güvenlik ilkesini belirlemede kullandığı kanıt hakkında daha fazla bilgi için bkz. [kanıt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)). Bilgisayar sistemlerini kötü amaçlı koddan korumanıza yardımcı olur ve güvenilen kodun kasıtlı olarak veya yanlışlıkla güvenliği tehlikeye atmasını sağlar. Kod erişimi güvenliği, uygulamanızın gerçekleştirebileceği işlemler üzerinde daha fazla denetim elde etmenizi sağlar, çünkü yalnızca uygulamanız için gerekli olan izinleri belirtebilirsiniz. Kod erişim güvenliği, ortak dil çalışma zamanını hedefleyen tüm yönetilen kodları etkiler ve bu kod tek bir kod erişim-güvenlik izni denetimi yapmasa bile. .NET Framework güvenlik hakkında daha fazla bilgi için bkz. [temel güvenlik kavramları](../../standard/security/key-security-concepts.md) ve [kod erişimi güvenlik temelleri](../misc/code-access-security-basics.md).

Kullanıcı bir Web sunucusunu veya bir dosya paylaşımından doğrudan bir Windows Forms yürütülebilir dosya çalıştırıyorsa, uygulamanıza verilen güven derecesi kodun bulunduğu yere ve nasıl başlatıldığına bağlıdır. Bir uygulama çalıştığında, otomatik olarak değerlendirilir ve ortak dil çalışma zamanından adlandırılmış bir izin kümesi alır. Varsayılan olarak, yerel bilgisayardaki koda tam güven izin kümesi verilir, yerel bir ağdan koda yerel Intranet izin kümesi verilir ve Internet 'ten koda Internet izin kümesi verilir.

> [!NOTE]
> .NET Framework sürüm 1,0 Service Pack 1 ve Service Pack 2 ' de, Internet bölgesi kod grubu hiçbir şey izin kümesini alır. .NET Framework diğer tüm sürümlerinde Internet bölgesi kodu grubu Internet izinleri kümesini alır.
>
> Bu izin kümelerinin her birinde verilen varsayılan izinler, [varsayılan güvenlik ilkesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100)) konusunda listelenmiştir. Uygulamanın aldığı izinlere bağlı olarak, doğru şekilde çalışır veya bir güvenlik özel durumu oluşturur.
>
> Birçok Windows Forms uygulama ClickOnce kullanılarak dağıtılır. ClickOnce dağıtımı oluşturmak için kullanılan araçların, daha önce açıklanenden farklı güvenlik Varsayılanları vardır. Daha fazla bilgi için aşağıdaki tartışmaya bakın.

Uygulamanıza verilen gerçek izinler, güvenlik ilkesi değiştirilemediğinden varsayılan değerlerden farklı olabilir; Bu, uygulamanızın bir bilgisayarda izin alabileceği ancak başka bir bilgisayarda izni olabileceği anlamına gelir.

## <a name="developing-a-more-secure-windows-forms-application"></a>Daha güvenli bir Windows Forms uygulaması geliştirme

Güvenlik, uygulama geliştirmenin tüm adımlarında önemlidir. [Güvenli kodlama yönergelerini](../../standard/security/secure-coding-guidelines.md)inceleyerek ve izleyerek başlayın.

Ardından, uygulamanızın tam güvende çalışmasına mi yoksa kısmi güvende mi çalışacağını belirleyin. Uygulamanızı tam güvende çalıştırmak, yerel bilgisayardaki kaynaklara erişmeyi kolaylaştırır, ancak uygulamanızı güvenli kodlama yönergelerine göre tasarlayamazsınız ve geliştirirseniz uygulamanızı ve kullanıcılarını yüksek güvenlik risklerine açık hale getirir. ilerde. Uygulamanızı kısmi güvende çalıştırmak daha güvenli bir uygulama geliştirmeyi ve çok fazla riski azaltmayı kolaylaştırır, ancak belirli özelliklerin nasıl uygulanacağı konusunda daha fazla planlama yapılmasını gerektirir.

Kısmi güven (Internet veya yerel Intranet izin kümeleri) seçeneğini belirlerseniz, uygulamanızın bu ortamda nasıl davranmasını istediğinize karar verin. Windows Forms, yarı güvenilir bir ortamda özellikler uygulamak için alternatif ve daha güvenli yollar sağlar. Uygulamanızın veri erişimi gibi belirli kısımları, hem kısmi güven hem de tam güven ortamları için farklı şekilde tasarlanıp yazılabilir. Uygulama ayarları gibi bazı Windows Forms Özellikler Kısmi güvende çalışacak şekilde tasarlanmıştır. Daha fazla bilgi için bkz. [uygulama ayarlarına genel bakış](./advanced/application-settings-overview.md).

Uygulamanızda kısmi güvenle izin verilmesi gereken daha fazla izin varsa, ancak tam güvende çalıştırmak istemiyorsanız, yalnızca ihtiyacınız olan ek izinleri ele alırken kısmi güvende çalıştırabilirsiniz. Örneğin, kısmi güvende çalıştırmak istiyorsanız ancak uygulamanıza kullanıcının dosya sistemindeki bir dizine salt okuma erişimi verilmesi gerekiyorsa, yalnızca bu dizin için <xref:System.Security.Permissions.FileIOPermission> isteyebilirsiniz. Doğru şekilde kullanıldığında, bu yaklaşım uygulamanıza daha fazla işlevsellik verebilir ve kullanıcılarınıza yönelik güvenlik risklerini en aza indirebilir.

Kısmi güvende çalışacak bir uygulama geliştirirken, uygulamanızın hangi izinlerle çalışması gerektiğini ve uygulamanızın isteğe bağlı olarak hangi izinlere sahip olacağını takip edin. Tüm izinler bilindiğinde, uygulama düzeyinde izin için bildirim temelli bir istek yapmanız gerekir. İzin istemek, uygulamanız için gereken izinlere ve özel olarak istemediğiniz izinlere ilişkin .NET Framework çalışma zamanına bildirir. İzin isteme hakkında daha fazla bilgi için bkz. [Izinleri isteme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).

İsteğe bağlı izinler istediğinizde, uygulamanız kendisine izin verilmeyen bir eylem gerçekleştirdiğinde üretilecek olan güvenlik özel durumlarını işlemeniz gerekir. <xref:System.Security.SecurityException> uygun işleme, uygulamanızın çalışmaya devam edebilmesini sağlar. Uygulamanız özel durumu kullanarak bir özelliğin Kullanıcı için devre dışı bırakılıp bırakılmadığını tespit edebilir. Örneğin, bir uygulama gerekli dosya izni verilmezse **Kaydet** menü seçeneğini devre dışı bırakabilir.

Bazen, tüm uygun izinleri mi belirleyebileceğinizi bilmeniz zordur. Örneğin, yüzeyinde zararsız gösteren bir yöntem çağrısı (örneğin, yürütme sırasında belirli bir noktada dosya sistemine erişebilme). Uygulamanızı gerekli tüm izinlerle dağıtmadıysanız, masaüstünüzde hata ayıkladığınızda, ancak dağıtıldığında başarısız olduğunda bu durum iyi bir şekilde test edebilir. .NET Framework 2,0 SDK ve Visual Studio 2005, uygulamanın ihtiyacı olan izinleri hesaplamak için araçlar içerir: sırasıyla, MT. exe komut satırı aracı ve Izinleri hesapla özelliği.

Aşağıdaki konularda, ek Windows Forms güvenlik özellikleri açıklanır.

|Konu|Açıklama|
|-----------|-----------------|
|[Windows Forms daha güvenli dosya ve veri erişimi](more-secure-file-and-data-access-in-windows-forms.md) - |Kısmi güven ortamındaki dosyalara ve verilere nasıl erişebileceğinizi açıklar.|
|[Windows Forms daha güvenli yazdırma](more-secure-printing-in-windows-forms.md) - |Kısmi güven ortamındaki yazdırma özelliklerine nasıl erişebileceğinizi açıklar.|
|[Windows Forms ek güvenlik konularını](additional-security-considerations-in-windows-forms.md) - |Pencere işleme, Panoyu kullanma ve kısmi güven ortamındaki yönetilmeyen koda çağrı yapma işlemlerini açıklar.|

### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Uygun Izinlerle uygulama dağıtma

Bir istemci bilgisayara bir Windows Forms uygulaması dağıtmanın en yaygın yolu, uygulamanızın çalışması için gereken tüm bileşenleri açıklayan bir dağıtım teknolojisidir. ClickOnce, uygulamanızı oluşturan derlemeleri ve dosyaları ve ayrıca uygulamanızın gerektirdiği izinleri tanımlayan, bildirimler adlı XML dosyalarını kullanır.

ClickOnce, bir istemci bilgisayarda yükseltilmiş izinler istemek için iki teknoloji içerir. Her iki teknoloji de Authenticode sertifikalarının kullanımına dayanır. Sertifikalar, kullanıcılarınızın uygulamanın güvenilen bir kaynaktan geldiği bazı güvence sağlanmasına yardımcı olur.

Aşağıdaki tabloda bu teknolojiler açıklanmaktadır.

|Yükseltilmiş izin teknolojisi|Açıklama|
|------------------------------------|-----------------|
|İzin yükseltme|Uygulamanızı ilk kez çalıştırdığında kullanıcıya bir güvenlik iletişim kutusu ister. **Izin yükseltme** iletişim kutusu kullanıcıya uygulamayı kimin yayımladığını bildirir, böylece Kullanıcı BT 'ye ek güven verip vermeyeceğine dair bilinçli bir karar verebilir|
|Güvenilen uygulama dağıtımı|Bir istemci bilgisayarında yayımcının Authenticode sertifikasının tek seferlik bir yüklemesini gerçekleştiren sistem yöneticisini içerir. Bu noktadan itibaren, sertifikayla imzalanan tüm uygulamalar güvenilen olarak kabul edilir ve ek istem olmadan yerel bilgisayarda tam güvende çalışabilir.|

Hangi teknolojiyi seçeceğiniz, dağıtım ortamınıza göre değişir. Daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).

Varsayılan olarak, Visual Studio veya .NET Framework SDK araçları (Mage. exe ve MageUI. exe) kullanılarak dağıtılan ClickOnce uygulamaları, tam güvene sahip bir istemci bilgisayarda çalışacak şekilde yapılandırılmıştır. Uygulamanızı kısmi güven kullanarak dağıtıyorsanız veya yalnızca bazı ek izinleri kullanarak, bu varsayılan değişikliği yapmanız gerekir. Dağıtımınızı yapılandırırken Visual Studio veya .NET Framework SDK aracı MageUI. exe ile bunu yapabilirsiniz. MageUI. exe ' nin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Izlenecek yol: el ile bir ClickOnce uygulaması dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).  Ayrıca bkz. [nasıl yapılır: ClickOnce uygulaması Için özel Izinleri ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hafybdaa(v=vs.110)) veya [nasıl yapılır: ClickOnce uygulaması Için özel izinleri ayarlama](/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application).

ClickOnce ve Izin yükselmesinin güvenlik yönleri hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications). Güvenilen uygulama dağıtımı hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).

### <a name="testing-the-application"></a>Uygulamayı Test Etme

Visual Studio 'Yu kullanarak Windows Forms uygulamanızı dağıttıysanız, kısmi güvende hata ayıklamayı veya geliştirme ortamından kısıtlı bir izin kümesini etkinleştirebilirsiniz.  Ayrıca bkz. [nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Güvenliği](windows-forms-security.md)
- [Kod erişim güvenliği temelleri](../misc/code-access-security-basics.md)
- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
- [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
