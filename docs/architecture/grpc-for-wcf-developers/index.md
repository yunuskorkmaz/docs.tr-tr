---
title: WCF Geliştiricileri için ASP.NET Core gRPC - WCF Geliştiricileri için gRPC
description: WCF geliştiricileri için Core 3.0'ASP.NET gRPC hizmetleri oluşturmaya giriş
ms.date: 09/02/2019
ms.openlocfilehash: 175dfbf1880a0937615543c248fba3bed0e25c23
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988966"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>WCF Geliştiricileri için ASP.NET Core gRPC

![kapak resmi](./media/cover.png)

YAYIMLAYAN

Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © 2019 Microsoft Corporation tarafından

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari https://www.microsoft.com Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.

Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.

Yazar:

> **Mark Rendle** - Baş Teknik Sorumlu - [Görsel Recode](https://visualrecode.com)
>
> **Miranda Steiner** - Teknik Yazar

Düzenleyicisi:

> **Maira Wenzel** - Sr. İçerik Geliştiricisi - Microsoft

## <a name="introduction"></a>Giriş

gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmak için modern bir çerçevedir. Windows Communication Foundation (WCF) NetTCP bağlamalarının performansını, SOAP'ın çapraz platform birlikte çalışabilirliğiyle birleştiğinde düşünün. gRPC, uygulamalar ve hizmetler arasında yüksek performanslı, düşük bant genişliğine bağlı iletişim sağlamak için HTTP/2 ve Protobuf ileti kodlama protokolü üzerine inşa edilmiştir. .NET, Java, Python, Node.js, Go ve C++ gibi en popüler programlama dilleri ve platformlarında sunucu ve istemci kodu oluşturmayı destekler. ASP.NET Core 3.0'da gRPC için birinci sınıf desteği, .NET 4.x için mevcut gRPC araçları ve kütüphanelerinin yanı sıra, organizasyonlarında .NET Core'u benimsemek isteyen geliştirme ekipleri için WCF'ye mükemmel bir alternatiftir.

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalı?

Bu kılavuz, .NET Framework veya .NET Core'da daha önce WCF kullanan ve uygulamalarını .NET Core 3.0 ve sonraki sürümler için modern bir RPC ortamına geçirmek isteyen geliştiriciler için yazılmıştır. Daha genel olarak, .NET Core 3.0'a yükseltme veya yükseltme yi düşünüyorsanız ve yerleşik gRPC araçlarını kullanmak istiyorsanız, bu kılavuz da yararlıdır.

## <a name="how-you-can-use-this-guide"></a>Bu kılavuzu nasıl kullanabilirsiniz?

Bu, ASP.NET Core 3.0'da gRPC Hizmetleri oluşturmaya kısa bir giriştir ve özellikle wcf'ye benzer bir platform olarak atıfta bulunulmaktadır. Her kavramı WCF'nin eşdeğer özellikleriyle ilişkilendiren gRPC ilkelerini açıklar ve mevcut bir WCF uygulamasını gRPC'ye geçirmek için kılavuz sunar. Ayrıca, WCF ile deneyime sahip olan ve yeni hizmetler oluşturmak için gRPC öğrenmek isteyen geliştiriciler için de yararlıdır. Örnek uygulamaları kendi projeleriniz için bir şablon veya başvuru olarak kullanabilirsiniz ve kitaptan veya örneklerinden kodu kopyalayıp yeniden kullanmakta özgürüz.

Bu hususların ve fırsatların ortak bir şekilde anlaşılmasını sağlamaya yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin. Herkesin ortak bir terimler ve temel ilkeler kümesinden çalışması mimari örüntülerin ve uygulamaların tutarlı bir şekilde uygulanmasını sağlamaya yardımcı olur.

## <a name="references"></a>Başvurular

- **gRPC web sitesi**
  <https://grpc.io>
- **Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapmak**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
