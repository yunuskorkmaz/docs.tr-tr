---
title: .NET Core 'da .NET Framework teknolojileri kullanılamıyor
titleSuffix: ''
description: .NET Core 'da kullanılamayan .NET Framework teknolojileri hakkında bilgi edinin
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: b75d946b9436b1075a068494b941fbdea5970e42
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795605"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 'da .NET Framework teknolojileri kullanılamıyor

.NET Framework kitaplıkları için kullanılabilen çeşitli teknolojiler, uygulama etki alanları, uzaktan Iletişim, kod erişim güvenliği (CAS), güvenlik saydamlığı ve System. EnterpriseServices gibi .NET Core ile birlikte kullanılamaz. Kitaplıklarınız Bu teknolojilerden birini veya birkaçını kullanıyorsa, aşağıda özetlenen diğer yaklaşımları göz önünde bulundurun. API uyumluluğu hakkında daha fazla bilgi için bkz. [.NET Core son değişiklikler](../compatibility/breaking-changes.md).

Bir API veya teknoloji şu anda uygulanmadığından, kasıtlı olarak desteklenmeyen anlamına gelmez. Karşılaştığınız belirli bir sorunun tasarım ile olup olmadığını görmek için GitHub depolarında .NET Core ' u arayın. Böyle bir gösterge bulamazsanız, belirli API 'Ler ve teknolojiler istemek için [DotNet/Runtime deposunda](https://github.com/dotnet/runtime/issues) bir sorun verin.

## <a name="appdomains"></a>Uygulama

Uygulama etki alanları (AppDomain), uygulamaları birbirinden ayırır. AppDomain, çalışma zamanı desteği gerektirir ve genellikle pahalıdır. Ek uygulama etki alanlarının oluşturulması desteklenmez ve gelecekte bu yeteneği eklemek için herhangi bir plan yoktur. Kod yalıtımı için alternatif olarak ayrı süreçler veya kapsayıcılar kullanın. Derlemeleri dinamik olarak yüklemek için <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfını kullanın.

Kod .NET Framework geçişini daha kolay hale getirmek için .NET Core, bazı <xref:System.AppDomain> API yüzeyini gösterir. API 'lerden <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>bazıları normal olarak çalışır (örneğin,), bazı Üyeler hiçbir şey yapmaz ( <xref:System.AppDomain.SetCachePath%2A>Örneğin,) ve bazıları <xref:System.PlatformNotSupportedException> (örneğin, <xref:System.AppDomain.CreateDomain%2A>). [DotNet/Runtime GitHub deposundaki](https://github.com/dotnet/runtime) [ `System.AppDomain` başvuru kaynağına](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) karşı kullandığınız türleri kontrol edin. Uygulanan sürümünüzle eşleşen dalı seçtiğinizden emin olun.

## <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan Iletişim, sorunlu bir mimari olarak tanımlandı. Bu, artık desteklenmeyen ilkeler arası iletişim için kullanılır. Ayrıca, uzaktan Iletişim için, bakım açısından pahalı olan çalışma zamanı desteği gerekir. Bu nedenlerden dolayı, .NET Core 'da .NET uzaktan Iletişim desteklenmez ve gelecekte bu hizmetin desteğini ekleme planlanmıyor.

İşlemler arasında iletişim için, <xref:System.IO.Pipes> sınıf veya <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> sınıf gıbı uzaktan iletişim (IPC) mekanizmalarını bir alternatif olarak düşünün.

Makineler arasında, alternatif olarak ağ tabanlı bir çözüm kullanın. Tercihen, HTTP gibi düşük yüklü bir düz metin protokolü kullanın. ASP.NET Core tarafından kullanılan Web sunucusu olan [Kestrel Web sunucusu](/aspnet/core/fundamentals/servers/kestrel), burada bir seçenektir. Ayrıca, ağ tabanlı <xref:System.Net.Sockets> , makineler arası senaryolar için kullanmayı düşünün. Daha fazla seçenek için bkz. [.net açık kaynak geliştirici projeleri: mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Yönetilen bir uygulamanın veya kitaplığın hangi kaynakları kullanacağını veya çalıştığını kısıtlamak için çalışma zamanına veya çerçeveye dayanan korumalı alana alma, [.NET Framework desteklenmez](../../framework/misc/code-access-security.md) ve bu nedenle de .NET Core üzerinde desteklenmez. .NET Framework ve bir ayrıcalık yükselmesinin bir güvenlik sınırı olarak kabul etmesine devam etmek için ayrıcalıkların yükseltilme gerçekleştiği çalışma zamanında çok fazla durum vardır. Bunlara ek olarak, CA 'LAR uygulamayı daha karmaşık hale getirir ve genellikle onu kullanmayı düşünmediğiniz uygulamalar için doğruluk performansına yönelik etkileri vardır.

Minimum ayrıcalık kümesi olan süreçler çalıştırmak için sanallaştırma, kapsayıcılar veya Kullanıcı hesapları gibi işletim sistemi tarafından belirtilen güvenlik sınırlarını kullanın.

## <a name="security-transparency"></a>Güvenlik saydamlığı

CA 'lara benzer şekilde, güvenlik saydamlığı, korumalı kodu bildirimle güvenlik açısından kritik koddan ayırır, ancak [artık güvenlik sınırı olarak desteklenmez](../../framework/misc/security-transparent-code.md). Bu özellik Silverlight tarafından yoğun bir şekilde kullanılır.

En az ayrıcalık kümesine sahip süreçler çalıştırmak için sanallaştırma, kapsayıcılar veya Kullanıcı hesapları gibi işletim sistemi tarafından belirtilen güvenlik sınırlarını kullanın.

## <a name="systementerpriseservices"></a>System. EnterpriseServices

System. EnterpriseServices (COM+), .NET Core tarafından desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework .NET Core 'a taşıma ile genel bakış](index.md)
