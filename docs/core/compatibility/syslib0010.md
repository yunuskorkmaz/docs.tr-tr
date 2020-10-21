---
title: SYSLIB0010 uyarısı
description: Derleme zamanı uyarı SYSLIB0010 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dcd331aa5c68381ea29848bc54ee4b1a5e75330d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333330"
---
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010: desteklenmeyen uzaktan iletişim API 'Leri

[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) eski bir teknolojidir ve altyapının yalnızca .NET Framework vardır. Aşağıdaki Remoting ile ilgili API 'Ler, .NET 5,0 ' den itibaren eski olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0010` derleme zamanında uyarı oluşturur.

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a>Geçici çözüm

Diğer uygulamalardaki veya makinelerde bulunan nesnelerle iletişim kurmak için WCF veya HTTP tabanlı REST hizmetlerini kullanmayı göz önünde bulundurun. Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../porting/net-framework-tech-unavailable.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
