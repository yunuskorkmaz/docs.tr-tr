---
title: .NET framework teknolojilerini .NET Core üzerinde kullanılamaz
description: .NET Core üzerinde kullanılabilir olan .NET Framework teknolojileri hakkında bilgi edinin
author: cartermp
ms.author: mairaw
ms.date: 12/7/2018
ms.openlocfilehash: 8b43c15a942e0effab486e5399325bec746484a2
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904907"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET framework teknolojilerini .NET Core üzerinde kullanılamaz

.NET Framework kitaplıkları için çeşitli teknolojilerden, uygulama etki alanları, uzaktan iletişim, kod erişim güvenliği (CAS) ve güvenlik gibi .NET Core ile kullanmak için kullanılamaz. Kitaplıklarınızı bir veya daha fazla teknolojiler kullanıyorsa, aşağıda ana hatlarıyla belirtilen alternatif yaklaşımlar göz önünde bulundurun. Corefx'te takım API uyumluluğu hakkında daha fazla bilgi için tutan bir [davranış değişiklikleri/compat sonu ve kullanım dışı/eski API'ler listesi](https://github.com/dotnet/corefx/wiki/ApiCompat) github'da.

API veya teknoloji yalnızca şu anda uygulanmadı çünkü kasıtlı olarak desteklenmeyen var. kapsıyor değil. GitHub depoları karşılaştığınız bir sorunu tasarıma, ancak böyle bir göstergesi bulamazsanız, lütfen dosyası, bir sorunu görmek .NET Core için ilk arayacağı [dotnet/corefx'te depo sorunları](https://github.com/dotnet/corefx/issues) istemek için github'da Özel API'ler ve teknolojileri için. [Sorunları istekleri taşıma](https://github.com/dotnet/corefx/labels/port-to-core) ile işaretlenmiş `port-to-core` etiketi.

## <a name="appdomains"></a>AppDomains

Uygulama etki alanları (uygulama etki alanları) uygulamaları birbirinden yalıtın. Uygulama etki alanları, çalışma zamanı desteği gerektirir ve genellikle oldukça pahalıdır. Ek uygulama etki alanları oluşturma desteklenmiyor... Gelecekte bu özelliği eklemeyi planlıyoruz yok. Kod bir ayırma işlemi için ayrı işlemler öneririz veya alternatif olarak kapsayıcıları kullanma. Dinamik derlemeler yüklenmesi için yeni öneririz <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfı.

.NET Framework'ten kod geçişi kolaylaştırmak için .NET Core bazı sunan <xref:System.AppDomain> API yüzeyi. Bazı API'leri işlev normal olarak (örneğin, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), bazı üyeleri hiçbir şey yapma (örneğin, <xref:System.AppDomain.SetCachePath%2A>), ve bunlardan bazıları throw <xref:System.PlatformNotSupportedException> (örneğin, <xref:System.AppDomain.CreateDomain%2A>). Kullandığınız karşı türlerini işaretleyin [ `System.AppDomain` başvuru kaynağı](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) içinde [dotnet/corefx'te GitHub deposu](https://github.com/dotnet/corefx)ettiğinizden emin uygulanan sürümünüzle eşleşen dalı seçin.

## <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan iletişim sorunlu bir mimari belirlenmiştir. Bu, artık desteklenmeyen AppDomain arası iletişim için kullanılır. Ayrıca, uzaktan iletişimi sürdürmek pahalı olan çalışma zamanı desteği gerektirir. Bu nedenlerle, .NET Core, .NET uzaktan iletişim desteklenmez ve gelecekte destek eklemeyi planlıyoruz yok.

İşlemler arasında iletişim için işlemler arası iletişim (IPC) mekanizmasını Remoting, alternatif olarak gibi göz önünde bulundurun <xref:System.IO.Pipes> veya <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> sınıfı.

Makine arasında ağ tabanlı bir çözüm alternatif olarak kullanın. Tercihen, HTTP gibi bir düşük ek yük düz metin protokol kullanın. [Kestrel web sunucusu](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), ASP.NET Core tarafından kullanılan web sunucusu, burada bir seçenektir. Ayrıca kullanmayı <xref:System.Net.Sockets> ağ tabanlı, makineler arası senaryolar için. Daha fazla seçenek için bkz: [.NET açık kaynak Geliştirici projeler: Mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Çalışma zamanı veya bir yönetilen uygulama veya kitaplık kullanır veya çalışan hangi kaynaklara sınırlamak için framework kullanan, korumalı alana alma [.NET Framework üzerinde desteklenmiyor](~/docs/framework/misc/code-access-security.md) ve .NET Core, bu nedenle de desteklenmez. CA güvenlik sınırı davranılması devam etmek için ayrıcalıkların oluştuğu .NET Framework ve çalışma zamanı içinde çok fazla durumlar vardır. Ayrıca, CA uygulaması daha karmaşık hale getirir ve genellikle doğruluk performans şifrelemelerini kullanmak istemediğiniz uygulamalar için.

En düşük ayrıcalık kümesi ile çalışan işlemleri için sanallaştırma, kapsayıcıları veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırları kullanın.

## <a name="security-transparency"></a>Güvenlik saydamlık

Benzer şekilde CA'ları, güvenlik saydamlık korumalı kod güvenlik kritik kod, bildirim temelli bir biçimde ayırır ancak olan [artık bir güvenlik sınırı olarak desteklenen](~/docs/framework/misc/security-transparent-code.md). Bu özellik tarafından Silverlight yoğun olarak kullanılır. 

En az çalışan işlemleri için sanallaştırma, kapsayıcıları veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırları kullanmanız ayrıcalık kümesi.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
