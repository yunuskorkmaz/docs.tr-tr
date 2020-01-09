---
title: .NET Core 'da .NET Framework teknolojileri kullanılamıyor
description: .NET Core 'da kullanılamayan .NET Framework teknolojileri hakkında bilgi edinin
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 6c457812f04b8e6503e5162b9f1f6497e7ef83b1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343565"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 'da .NET Framework teknolojileri kullanılamıyor

.NET Framework kitaplıkları için kullanılabilen çeşitli teknolojiler, uygulama etki alanları, uzaktan Iletişim, kod erişim güvenliği (CAS), güvenlik saydamlığı ve System. EnterpriseServices gibi .NET Core ile birlikte kullanılamaz. Kitaplıklarınız Bu teknolojilerden birini veya birkaçını kullanıyorsa, aşağıda özetlenen diğer yaklaşımları göz önünde bulundurun. API uyumluluğu hakkında daha fazla bilgi için bkz. [.NET Core son değişiklikler](../compatibility/breaking-changes.md).

Bir API veya teknoloji şu anda uygulanmadığından, kasıtlı olarak desteklenmeyen anlamına gelmez. İlk olarak, karşılaştığınız belirli bir sorunun tasarım ile olup olmadığını görmek için GitHub depolarında .NET Core için arama yapmalısınız. Böyle bir göstergeyi bulamıyorsanız, lütfen belirli API 'Leri ve teknolojileri sormak için GitHub 'da [DotNet/corefx depo sorunlarında](https://github.com/dotnet/corefx/issues) bir sorun bildirin. [Sorunların taşıma istekleri](https://github.com/dotnet/corefx/labels/port-to-core) `port-to-core` etiketiyle işaretlenir.

## <a name="appdomains"></a>Uygulama

Uygulama etki alanları (AppDomain), uygulamaları birbirinden ayırır. AppDomain, çalışma zamanı desteği gerektirir ve genellikle oldukça pahalıdır. Ek uygulama etki alanlarının oluşturulması desteklenmez ve gelecekte bu yeteneği eklemek için herhangi bir plan yoktur. Kod yalıtımı için alternatif olarak ayrı süreçler veya kapsayıcılar kullanın. Derlemelerin dinamik yüklemesi için <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfını kullanın.

.NET Framework daha kolay bir şekilde kod geçişi yapmak için, .NET Core <xref:System.AppDomain> API yüzeyinden bazılarını ortaya çıkarır. API 'lerden bazıları normal olarak çalışır (örneğin, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), bazı Üyeler hiçbir şey yapmaz (örneğin, <xref:System.AppDomain.SetCachePath%2A>) ve bazıları <xref:System.PlatformNotSupportedException> oluşturmaz (örneğin, <xref:System.AppDomain.CreateDomain%2A>). Uygulanan sürümünüzle eşleşen dalı seçtiğinizden emin olmak için [DotNet/corefx GitHub deposundaki](https://github.com/dotnet/corefx) [`System.AppDomain` başvuru kaynağına](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) karşı kullandığınız türleri kontrol edin.

## <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan Iletişim, sorunlu bir mimari olarak tanımlandı. Bu, artık desteklenmeyen ilkeler arası iletişim için kullanılır. Ayrıca, uzaktan Iletişim için, bakım açısından pahalı olan çalışma zamanı desteği gerekir. Bu nedenlerden dolayı, .NET Core 'da .NET uzaktan Iletişim desteklenmez ve gelecekte bu hizmetin desteğini ekleme planlanmıyor.

İşlemler arasında iletişim için, <xref:System.IO.Pipes> sınıfı veya <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> sınıfı gibi uzaktan iletişim için bir alternatif olarak işlem temelli iletişim (IPC) mekanizmalarını göz önünde bulundurun.

Makineler arasında, alternatif olarak ağ tabanlı bir çözüm kullanın. Tercihen, HTTP gibi düşük yüklü bir düz metin protokolü kullanın. ASP.NET Core tarafından kullanılan Web sunucusu olan [Kestrel Web sunucusu](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), burada bir seçenektir. Ayrıca, ağ tabanlı, makineler arası senaryolar için <xref:System.Net.Sockets> kullanmayı düşünün. Daha fazla seçenek için bkz. [.net açık kaynak geliştirici projeleri: mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

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
