---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: WCF geliştiricileri için ASP.NET Core 3,0 ' de gRPC hizmetleri oluşturmaya giriş
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543241"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>WCF Geliştiricileri için ASP.NET Core gRPC

![kapak resmi](./media/cover.png)

YAYıMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2019 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür. Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.

Microsoft ve "ticari markalar" Web sayfasındaki https://www.microsoft.com listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Yazarlar:

> Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)
>
> **MDA bu,** teknik yazar

Düzenleyen:

> **Maira Wenzel** -SR. Content Developer-Microsoft

## <a name="introduction"></a>Giriş

gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmaya yönelik modern bir çerçevedir. SOAP 'ın platformlar arası birlikte çalışabilirliğiyle birlikte Windows Communication Foundation (WCF) NetTCP bağlamalarının performansını düşünün. , uygulamalar ve hizmetler arasında yüksek performans, düşük bant genişliğine sahip bir iletişim sağlamak için HTTP/2 ve prototip ileti kodlama protokolü üzerinde gRPC derlemeleri. .NET, Java, Python, Node. js, Go ve C++gibi popüler programlama dilleri ve platformları genelinde sunucu ve istemci kodu üretimini destekler. ASP.NET Core 3,0 ' de gRPC için birinci sınıf destek sayesinde, mevcut gRPC araçları ve .NET 4. x kitaplıklarının yanı sıra, kuruluşlarda .NET Core 'u benimsemek isteyen geliştirme ekiplerine yönelik WCF için mükemmel bir alternatiftir.

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuz, daha önce WCF kullanan .NET Framework veya .NET Core 'da çalışan geliştiriciler için yazılmıştır ve uygulamalarını .NET Core 3,0 ve üzeri sürümler için modern bir RPC ortamına geçirmeyi arayan kişiler. Daha genel olarak, yükseltme yapıyorsanız veya yükseltmeyi .NET Core 3,0 ' e ve yerleşik gRPC araçlarını kullanmak istiyorsanız, bu kılavuz de yararlı olur.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

Bu, ASP.NET Core 3,0 ' de gRPC hizmetlerini, benzer bir platform olarak WCF 'ye belirli bir şekilde oluşturmaya yönelik kısa bir giriş niteliğindedir. GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar. Ayrıca, WCF ile karşılaşan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de yararlıdır. Örnek uygulamaları kendi projeleriniz için bir şablon veya başvuru olarak kullanabilir ve kodu kitap veya örneklerinden kopyalayabilir ve yeniden kullanabilirsiniz.

Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin. Her birinin ortak bir terim kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.

## <a name="references"></a>Başvurular

- **GRPC Web sitesi**
  <https://grpc.io>
- **Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
