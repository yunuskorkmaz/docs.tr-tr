---
title: .NET 'te COM birlikte çalışması
description: .NET ' te COM kitaplıklarıyla birlikte çalışma hakkında bilgi edinin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 07/11/2019
ms.openlocfilehash: 9355e2ae84da623ffa725f5b2ac1bdee25b966d8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971887"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="595f8-103">.NET 'te COM birlikte çalışması</span><span class="sxs-lookup"><span data-stu-id="595f8-103">COM Interop in .NET</span></span>

<span data-ttu-id="595f8-104">Bileşen nesne modeli (COM), bir nesnenin işlevselliğini diğer bileşenlere sunma ve Windows platformlarında uygulamaları barındırmasına imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="595f8-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="595f8-105">Kullanıcıların mevcut kod tabanlarıyla birlikte çalışabilmelerini sağlamaya yardımcı olmak için .NET Framework, COM kitaplıklarıyla birlikte çalışmak üzere her zaman güçlü destek sağlamıştır.</span><span class="sxs-lookup"><span data-stu-id="595f8-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="595f8-106">.NET Core 3,0 ' de, Windows 'ta .NET Core 'a bu desteğin büyük bir bölümü eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="595f8-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="595f8-107">Buradaki belgelerde, ortak COM birlikte çalışma Techonologies nasıl çalıştığı ve mevcut COM kitaplıklarınız ile birlikte çalışmak için nasıl kullanabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="595f8-107">The documentation here will explain how the common COM interop techonologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="595f8-108">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="595f8-108">COM Wrappers</span></span>](./com-wrappers.md)
- [<span data-ttu-id="595f8-109">COM çağrılabilir sarmalayıcılar</span><span class="sxs-lookup"><span data-stu-id="595f8-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="595f8-110">Çalışma zamanı çağrılabilir sarmalayıcılar</span><span class="sxs-lookup"><span data-stu-id="595f8-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="595f8-111">COM birlikte çalışma için .NET türlerini nitelendirme</span><span class="sxs-lookup"><span data-stu-id="595f8-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
