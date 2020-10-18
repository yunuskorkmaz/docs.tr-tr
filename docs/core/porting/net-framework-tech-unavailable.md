---
title: .NET Core ve .NET 5 + üzerinde .NET Framework teknolojileri kullanılamıyor
titleSuffix: ''
description: .NET Core ve .NET 5,0 ve sonraki sürümlerde kullanılamayan .NET Framework teknolojileri hakkında bilgi edinin.
author: cartermp
ms.date: 10/13/2020
ms.openlocfilehash: 492aace9db3dc3acef18e995f10b7b5fbe251558
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161042"
---
# <a name="net-framework-technologies-unavailable-on-net-core-and-net-5"></a>.NET Core ve .NET 5 + üzerinde .NET Framework teknolojileri kullanılamıyor

.NET Framework kitaplıkları için kullanılabilen çeşitli teknolojiler, uygulama etki alanları, uzaktan iletişim, kod erişim güvenliği (CAS) ve güvenlik saydamlığı gibi .NET Core ve .NET 5,0 ve sonraki sürümlerle birlikte kullanılamaz <xref:System.EnterpriseServices?displayProperty=fullName> . Kitaplıklarınız Bu teknolojilerden birini veya birkaçını kullanıyorsa, burada özetlenen diğer yaklaşımları göz önünde bulundurun. API uyumluluğu hakkında daha fazla bilgi için bkz. [.net 'Teki son değişiklikler](../compatibility/breaking-changes.md).

> [!TIP]
> Bir API veya teknoloji şu anda uygulanmadığından, kasıtlı olarak desteklenmeyen anlamına gelmez. Karşılaştığınız belirli bir sorunun tasarım ile olup olmadığını görmek için .NET GitHub depolarında arama yapın. Böyle bir gösterge bulamazsanız, belirli API 'Ler ve teknolojiler istemek için [DotNet/Runtime deposunda](https://github.com/dotnet/runtime/issues) bir sorun verin.

## <a name="application-domains"></a>Uygulama etki alanları

Uygulama etki alanları (AppDomain), uygulamaları birbirinden ayırır. AppDomain, çalışma zamanı desteği gerektirir ve genellikle pahalıdır. Ek uygulama etki alanlarının oluşturulması desteklenmez ve gelecekte bu yeteneği eklemek için herhangi bir plan yoktur. Kod yalıtımı için alternatif olarak ayrı süreçler veya kapsayıcılar kullanın. Derlemeleri dinamik olarak yüklemek için sınıfını kullanın <xref:System.Runtime.Loader.AssemblyLoadContext> .

Kod .NET Framework geçişini daha kolay hale getirmek için .NET 5 +, bazı <xref:System.AppDomain> API yüzeyini kullanıma sunar. API 'lerden bazıları normal olarak çalışır (örneğin, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> ), bazı Üyeler hiçbir şey yapmaz (örneğin,) <xref:System.AppDomain.SetCachePath%2A> ve bazıları <xref:System.PlatformNotSupportedException> (örneğin, <xref:System.AppDomain.CreateDomain%2A> ). [DotNet/Runtime GitHub deposundaki](https://github.com/dotnet/runtime) [ `System.AppDomain` başvuru kaynağına](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) karşı kullandığınız türleri kontrol edin. Uygulanan sürümünüzle eşleşen dalı seçtiğinizden emin olun.

## <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan iletişim, sorunlu bir mimari olarak tanımlandı. Artık desteklenmeyen uygulama etki alanları arasında iletişim kurmak için kullanılır. Ayrıca, uzaktan iletişim için, bakım açısından pahalı olan çalışma zamanı desteği gerekir. Bu nedenlerden dolayı .NET Remoting .NET Core ve .NET 5 + ' da desteklenmez ve gelecekte bu hizmetin desteğini ekleme planlanmıyor.

İşlemler arasında iletişim için, sınıf veya sınıf gibi uzaktan iletişim (IPC) mekanizmalarını bir alternatif olarak düşünün <xref:System.IO.Pipes> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> .

Makineler arasında, alternatif olarak ağ tabanlı bir çözüm kullanın. Tercihen, HTTP gibi düşük yüklü bir düz metin protokolü kullanın. ASP.NET Core tarafından kullanılan Web sunucusu olan [Kestrel Web sunucusu](/aspnet/core/fundamentals/servers/kestrel)burada bir seçenektir. Ayrıca, <xref:System.Net.Sockets> ağ tabanlı, makineler arası senaryolar için kullanmayı düşünün. Daha fazla seçenek için bkz. [.net açık kaynak geliştirici projeleri: mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Kod erişim güvenliği (CAS)

Yönetilen bir uygulamanın veya kitaplığın hangi kaynakları kullanacağını veya çalıştığını kısıtlamak için çalışma zamanına veya çerçeveye dayanan korumalı alana alma, [.NET Framework desteklenmez](../../framework/misc/code-access-security.md) ve bu nedenle de .NET Core ve .NET 5 + ' da desteklenmez. .NET Framework ve bir ayrıcalık yükselmesinin bir güvenlik sınırı olarak kabul etmesine devam etmek için ayrıcalıkların yükseltilme gerçekleştiği çalışma zamanında çok fazla durum vardır. Bunlara ek olarak, CA 'LAR uygulamayı daha karmaşık hale getirir ve genellikle onu kullanmayı düşünmediğiniz uygulamalar için doğruluk performansına yönelik etkileri vardır.

Minimum ayrıcalık kümesi olan süreçler çalıştırmak için sanallaştırma, kapsayıcılar veya Kullanıcı hesapları gibi işletim sistemi tarafından belirtilen güvenlik sınırlarını kullanın.

## <a name="security-transparency"></a>Güvenlik saydamlığı

CA 'lara benzer şekilde, güvenlik saydamlığı, korumalı kodu bildirimle güvenlik açısından kritik koddan ayırır, ancak [artık güvenlik sınırı olarak desteklenmez](../../framework/misc/security-transparent-code.md). Bu özellik Silverlight tarafından yoğun bir şekilde kullanılır.

En az ayrıcalık kümesine sahip süreçler çalıştırmak için sanallaştırma, kapsayıcılar veya Kullanıcı hesapları gibi işletim sistemi tarafından belirtilen güvenlik sınırlarını kullanın.

## <a name="systementerpriseservices"></a>System. EnterpriseServices

<xref:System.EnterpriseServices?displayProperty=fullName> (COM+), .NET Core ve .NET 5 + tarafından desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework .NET Core 'a taşıma ile genel bakış](index.md)
