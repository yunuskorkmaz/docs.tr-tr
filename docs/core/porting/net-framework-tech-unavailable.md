---
title: .NET Framework teknolojileri .NET Core'da kullanılamıyor
titleSuffix: ''
description: .NET Core'da kullanılamayan .NET Framework teknolojileri hakkında bilgi edinin
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 7dfec63870950f12ec933ebf09041b3c8ce2cbb5
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607803"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Framework teknolojileri .NET Core'da kullanılamıyor

.NET Framework kitaplıkları için kullanılabilen AppDomains, Remoting, Code Access Security (CAS), Security Transparency ve System.EnterpriseServices gibi .NET Core ile birlikte kullanılamaz. Kitaplıklarınız bu teknolojilerden birine veya daha fazlasını güveniyorsa, aşağıda özetlenen alternatif yaklaşımları göz önünde bulundurun. API uyumluluğu hakkında daha fazla bilgi için [.NET Core kesme değişiklikleri'ne](../compatibility/breaking-changes.md)bakın.

Bir API veya teknolojinin şu anda uygulanmamış olması, uygulamanın kasıtlı olarak desteklenmediği anlamına gelmez. Karşılaştığınız belirli bir sorunun tasarım adedi olup olmadığını görmek için .NET Core için GitHub depolarını arayın. Böyle bir gösterge bulamazsanız, belirli API'ler ve teknolojiler istemek için [dotnet/runtime deposunda](https://github.com/dotnet/runtime/issues) bir sorun dosya. İstekleri taşıma [sorunları, bağlantı noktası-çekirdek](https://github.com/dotnet/runtime/labels/port-to-core) etiketiyle işaretlenir.

## <a name="appdomains"></a>AppDomains

Uygulama etki alanları (AppDomains) uygulamaları birbirinden yalıtır. AppDomains çalışma zamanı desteği gerektirir ve genellikle oldukça pahalıdır. Ek uygulama etki alanları oluşturma desteklenmez ve gelecekte bu özelliği eklemek için herhangi bir plan yoktur. Kod yalıtımı için alternatif olarak ayrı işlemler veya kapsayıcılar kullanın. Derlemeleri dinamik olarak yüklemek <xref:System.Runtime.Loader.AssemblyLoadContext> için sınıfı kullanın.

.NET Framework'den kod geçişini kolaylaştırmak için .NET <xref:System.AppDomain> Core, API yüzeyinin bir kısmını ortaya çıkarır. API'lerin bazıları normal olarak çalışır <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>(örneğin), bazı üyeler <xref:System.AppDomain.SetCachePath%2A>hiçbir şey yapmaz <xref:System.PlatformNotSupportedException> (örneğin), <xref:System.AppDomain.CreateDomain%2A>bazıları atar (örneğin, ). [Dotnet/runtime GitHub deposundaki](https://github.com/dotnet/runtime) [ `System.AppDomain` başvuru kaynağıyla](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) karşı kullandığınız türleri denetleyin. Uygulanan sürümünizle eşleşen dalı seçtiğinizden emin olun.

## <a name="remoting"></a>Remoting

.NET Remoting sorunlu bir mimari olarak tanımlanmıştı. Artık desteklenmeyen çapraz AppDomain iletişimi için kullanılır. Ayrıca, Remoting korumak için pahalı çalışma zamanı desteği gerektirir. Bu nedenlerden dolayı,.NET Remoting .NET Core'da desteklenmez ve gelecekte buna destek eklemeyi planlamamayız.

Süreçler arası iletişim için, sınıflar veya <xref:System.IO.Pipes> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> sınıf gibi Remoting'e alternatif olarak süreçler arası iletişim (IPC) mekanizmalarını düşünün.

Makineler arasında, alternatif olarak ağ tabanlı bir çözüm kullanın. Tercihen, HTTP gibi düşük tepeli düz metin protokolü kullanın. [Kestrel web sunucusu](/aspnet/core/fundamentals/servers/kestrel), ASP.NET Core tarafından kullanılan web sunucusu, burada bir seçenektir. Ayrıca, ağ <xref:System.Net.Sockets> tabanlı, makineler arası senaryolar için kullanmayı düşünün. Daha fazla seçenek için [bkz.](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging)

## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Yönetilen bir uygulamanın veya kitaplığın kullandığı veya çalıştırdığı kaynakları kısıtlamak için çalışma süresine veya çerçeveye dayanan Sandboxing, [.NET Framework'de desteklenmez](../../framework/misc/code-access-security.md) ve bu nedenle .NET Core'da da desteklenmez. .NET Framework'de ve cas'ı güvenlik sınırı olarak ele almaya devam etmek için ayrıcalıkların yükseltilmesinin gerçekleştiği çalışma zamanında çok fazla durum vardır. Buna ek olarak, CAS uygulamayı daha karmaşık hale getirir ve genellikle kullanmak istemeyen uygulamalar için doğruluk-performans etkileri ne kadar dır?

İşlemleri en az ayrıcalık kümesiyle çalıştırmak için sanallaştırma, kapsayıcılar veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırlarını kullanın.

## <a name="security-transparency"></a>Güvenlik Şeffaflığı

CAS'a benzer şekilde, Güvenlik Saydamlığı da sandboxed kodu güvenlik kritik kodundan bildirimsel bir şekilde ayırır, ancak [artık güvenlik sınırı olarak desteklenmez.](../../framework/misc/security-transparent-code.md) Bu özellik Silverlight tarafından yoğun olarak kullanılmaktadır.

En az ayrıcalık kümesine sahip işlemleri çalıştırmak için sanallaştırma, kapsayıcılar veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırlarını kullanın.

## <a name="systementerpriseservices"></a>Enterpriseservices

System.EnterpriseServices (COM+) .NET Core tarafından desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'den .NET Core'a taşımaya genel bakış](../porting/index.md)
