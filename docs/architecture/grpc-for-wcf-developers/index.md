---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: YAZıLACAK
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: dc39fc96e7154fb50acd0b65a58586b3fa12ab50
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696914"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>WCF Geliştiricileri için ASP.NET Core gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

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

Microsoft ve "ticari markalar" Web sayfasında https://www.microsoft.com konumunda listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Geliştirici

> Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)
>
> **MDA bu,** teknik yazar

Edit

> **Maira Wenzel** -SR içerik geliştiricisi-Microsoft

## <a name="introduction"></a>Giriş

TODO

## <a name="purpose"></a>Amaç

TODO

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

**BUNU GÜNCELLEŞTIR**

Bu kılavuzun hedef kitlesi, .NET 4 ve önceki sürümlerde WCF çözümlerini, gRPC hizmetlerini kullanarak ASP.NET Core 3,0 ' ye geçirmeye ilgilenen WCF geliştiricileri, geliştirme müşteri adayları ve mimarlardır.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

**BUNU GÜNCELLEŞTIR**

Bu, WCF 'ye benzer bir platform olarak belirli bir başvuru ile ASP.NET Core 3,0 ' de gRPC hizmetleri oluşturmaya yönelik kısa bir giriş niteliğindedir. GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar. Ayrıca, WCF deneyimi olan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de kullanışlıdır. Örnek uygulama, kendi projeleriniz için bir şablon veya başvuru olarak veya defterden veya örneklerinden kodu kopyalayıp yeniden kullandığınızda ücretsiz olarak kullanılabilir.

Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin. Her bir gövdenin ortak bir terminoloji kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.

## <a name="references"></a>Referanslar

- **gRPC Web sitesi**  
  <https://grpc.io>
- **Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)
