---
title: .NET Core 'da .NET Framework teknolojileri kullanılamıyor
description: .NET Core 'da kullanılamayan .NET Framework teknolojileri hakkında bilgi edinin
author: cartermp
ms.author: mairaw
ms.date: 04/30/2019
ms.openlocfilehash: 87c3dd337ad44fd21b255afa7c03b528cd8a42ad
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660607"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 'da .NET Framework teknolojileri kullanılamıyor

.NET Framework kitaplıkları için kullanılabilen çeşitli teknolojiler, uygulama etki alanları, uzaktan Iletişim, kod erişim güvenliği (CAS) ve güvenlik saydamlığı gibi .NET Core ile birlikte kullanılamaz. Kitaplıklarınız Bu teknolojilerden birini veya birkaçını kullanıyorsa, aşağıda özetlenen diğer yaklaşımları göz önünde bulundurun. API uyumluluğu hakkında daha fazla bilgi için CoreFX ekibi, GitHub 'da [davranış değişikliklerinin/uyumluluk sonlarının ve kullanım dışı/eski API](https://github.com/dotnet/corefx/wiki/ApiCompat) 'Lerin bir listesini tutar.

Bir API veya teknoloji şu anda uygulanmadığından, kasıtlı olarak desteklenmeyen anlamına gelmez. İlk olarak .NET Core için GitHub depolarında arama yapmanız gerekir, ancak bu tür bir göstergeyi bulamazsanız, lütfen GitHub 'daki [DotNet/corefx depo sorunlarını](https://github.com/dotnet/corefx/issues) Izleyerek belirli API 'ler için sorun giderin ve teknolojilerinin. [Sorunların taşıma istekleri](https://github.com/dotnet/corefx/labels/port-to-core) `port-to-core` etiketle işaretlenir.

## <a name="appdomains"></a>Uygulama

Uygulama etki alanları (AppDomain), uygulamaları birbirinden ayırır. AppDomain, çalışma zamanı desteği gerektirir ve genellikle oldukça pahalıdır. Ek uygulama etki alanlarının oluşturulması desteklenmez. Gelecekte bu özelliği eklemeyi planlıyoruz. Kod yalıtımı için, farklı süreçler veya kapsayıcılar kullanmanın alternatif olarak kullanılması önerilir. Derlemelerin dinamik yüklemesi için yeni <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfı öneririz.

Kod .NET Framework geçişini daha kolay hale getirmek için .NET Core, bazı <xref:System.AppDomain> API yüzeyini gösterir. API 'lerden bazıları normal olarak çalışır <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>(örneğin,), bazı Üyeler hiçbir şey yapmaz ( <xref:System.AppDomain.SetCachePath%2A>Örneğin,) <xref:System.PlatformNotSupportedException> ve bazıları (örneğin, <xref:System.AppDomain.CreateDomain%2A>). Uygulanan sürümünüzle eşleşen dalı seçtiğinizden emin olmak için [DotNet/corefx GitHub deposundaki](https://github.com/dotnet/corefx) [ `System.AppDomain` başvuru kaynağına](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) karşı kullandığınız türleri kontrol edin.

## <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan Iletişim, sorunlu bir mimari olarak tanımlandı. Bu, artık desteklenmeyen ilkeler arası iletişim için kullanılır. Ayrıca, uzaktan Iletişim için, bakım açısından pahalı olan çalışma zamanı desteği gerekir. Bu nedenlerden dolayı, .NET Core 'da .NET uzaktan Iletişim desteklenmez ve gelecekte bu hizmetin desteğini ekleme planlanmıyor.

İşlemler arasında iletişim için, <xref:System.IO.Pipes> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> veya sınıfı gibi uzaktan iletişim (IPC) mekanizmalarını bir alternatif olarak düşünün.

Makineler arasında, alternatif olarak ağ tabanlı bir çözüm kullanın. Tercihen, HTTP gibi düşük yüklü bir düz metin protokolü kullanın. ASP.NET Core tarafından kullanılan Web sunucusu olan [Kestrel Web sunucusu](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), burada bir seçenektir. Ayrıca, ağ <xref:System.Net.Sockets> tabanlı, platformlar arası senaryolar için kullanmayı düşünün. Daha fazla seçenek için bkz [. .net açık kaynak geliştirici projeleri: Mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Yönetilen bir uygulamanın veya kitaplığın hangi kaynakları kullanacağını veya çalıştığını kısıtlamak için çalışma zamanına veya çerçeveye dayanan korumalı alana alma, [.NET Framework desteklenmez](../../framework/misc/code-access-security.md) ve bu nedenle de .NET Core üzerinde desteklenmez. .NET Framework ve bir ayrıcalık yükselmesinin bir güvenlik sınırı olarak kabul etmesine devam etmek için ayrıcalıkların yükseltilme gerçekleştiği çalışma zamanında çok fazla durum vardır. Bunlara ek olarak, CA 'LAR uygulamayı daha karmaşık hale getirir ve genellikle onu kullanmayı düşünmediğiniz uygulamalar için doğruluk performansına yönelik etkileri vardır.

İşletim sistemi tarafından sunulan sanallaştırma, kapsayıcılar veya minimum ayrıcalık kümesi ile işlem çalıştırmak için Kullanıcı hesapları gibi güvenlik sınırlarını kullanın.

## <a name="security-transparency"></a>Güvenlik saydamlığı

CA 'lara benzer şekilde, güvenlik saydamlığı, korumalı kodu bildirimle güvenlik açısından kritik koddan ayırır, ancak [artık güvenlik sınırı olarak desteklenmez](../../framework/misc/security-transparent-code.md). Bu özellik Silverlight tarafından yoğun bir şekilde kullanılır. 

İşletim sistemi tarafından sunulan sanallaştırma, kapsayıcılar veya en az ayrıcalık kümesiyle işlem çalıştırmak için Kullanıcı hesapları gibi güvenlik sınırlarını kullanın.

## <a name="systementerpriseservices"></a>System. EnterpriseServices

System. EnterpriseServices (COM+), .NET Core tarafından desteklenmez.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
