---
title: SYSLIB0010 uyarısı
description: Derleme zamanı uyarı SYSLIB0010 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 289fb3f766a6e1d37bea8faec1896d20442f43f9
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596557"
---
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010: desteklenmeyen uzaktan iletişim API 'Leri

[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) eski bir teknolojidir ve altyapının yalnızca .NET Framework vardır. Aşağıdaki Remoting ile ilgili API 'Ler, .NET 5,0 ' den itibaren eski olarak işaretlenir. Kod içinde kullanmak, `SYSLIB0010` derleme zamanında uyarı oluşturur.

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a>Geçici Çözümler

Diğer uygulamalardaki veya makinelerde bulunan nesnelerle iletişim kurmak için WCF veya HTTP tabanlı REST hizmetlerini kullanmayı göz önünde bulundurun. Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../porting/net-framework-tech-unavailable.md).

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
