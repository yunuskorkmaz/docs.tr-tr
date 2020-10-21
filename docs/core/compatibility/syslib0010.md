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
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="11626-103">SYSLIB0010: desteklenmeyen uzaktan iletişim API 'Leri</span><span class="sxs-lookup"><span data-stu-id="11626-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="11626-104">[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) eski bir teknolojidir ve altyapının yalnızca .NET Framework vardır.</span><span class="sxs-lookup"><span data-stu-id="11626-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="11626-105">Aşağıdaki Remoting ile ilgili API 'Ler, .NET 5,0 ' den itibaren eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="11626-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="11626-106">Kod içinde kullanmak, `SYSLIB0010` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11626-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="11626-107">Geçici çözüm</span><span class="sxs-lookup"><span data-stu-id="11626-107">Workaround</span></span>

<span data-ttu-id="11626-108">Diğer uygulamalardaki veya makinelerde bulunan nesnelerle iletişim kurmak için WCF veya HTTP tabanlı REST hizmetlerini kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="11626-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="11626-109">Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="11626-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11626-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11626-110">See also</span></span>

- <span data-ttu-id="11626-111">[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="11626-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
