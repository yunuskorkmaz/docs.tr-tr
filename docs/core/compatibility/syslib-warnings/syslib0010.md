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
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="43fd7-103">SYSLIB0010: desteklenmeyen uzaktan iletişim API 'Leri</span><span class="sxs-lookup"><span data-stu-id="43fd7-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="43fd7-104">[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) eski bir teknolojidir ve altyapının yalnızca .NET Framework vardır.</span><span class="sxs-lookup"><span data-stu-id="43fd7-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="43fd7-105">Aşağıdaki Remoting ile ilgili API 'Ler, .NET 5,0 ' den itibaren eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="43fd7-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="43fd7-106">Kod içinde kullanmak, `SYSLIB0010` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43fd7-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="43fd7-107">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="43fd7-107">Workarounds</span></span>

<span data-ttu-id="43fd7-108">Diğer uygulamalardaki veya makinelerde bulunan nesnelerle iletişim kurmak için WCF veya HTTP tabanlı REST hizmetlerini kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="43fd7-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="43fd7-109">Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="43fd7-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../../porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="43fd7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43fd7-110">See also</span></span>

- <span data-ttu-id="43fd7-111">[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="43fd7-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
