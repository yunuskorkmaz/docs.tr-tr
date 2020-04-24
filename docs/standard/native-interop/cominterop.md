---
title: .NET 'te COM birlikte çalışması
description: .NET ' te COM kitaplıklarıyla birlikte çalışma hakkında bilgi edinin.
ms.date: 07/11/2019
ms.openlocfilehash: 63205ae5c09d6c3929da13788eb781cd975ca814
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627380"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="9b6e5-103">.NET 'te COM birlikte çalışması</span><span class="sxs-lookup"><span data-stu-id="9b6e5-103">COM Interop in .NET</span></span>

<span data-ttu-id="9b6e5-104">Bileşen nesne modeli (COM), bir nesnenin işlevselliğini diğer bileşenlere sunma ve Windows platformlarında uygulamaları barındırmasına imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="9b6e5-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="9b6e5-105">Kullanıcıların mevcut kod tabanlarıyla birlikte çalışabilmelerini sağlamaya yardımcı olmak için .NET Framework, COM kitaplıklarıyla birlikte çalışmak üzere her zaman güçlü destek sağlamıştır.</span><span class="sxs-lookup"><span data-stu-id="9b6e5-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="9b6e5-106">.NET Core 3,0 ' de, Windows 'ta .NET Core 'a bu desteğin büyük bir bölümü eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9b6e5-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="9b6e5-107">Buradaki belgelerde, ortak COM birlikte çalışma teknolojilerinin nasıl çalıştığı ve mevcut COM kitaplıklarınız ile birlikte çalışmak için nasıl kullanabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9b6e5-107">The documentation here will explain how the common COM interop technologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="9b6e5-108">COM sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="9b6e5-108">COM Wrappers</span></span>](./com-wrappers.md)
- [<span data-ttu-id="9b6e5-109">COM çağrılabilir sarmalayıcılar</span><span class="sxs-lookup"><span data-stu-id="9b6e5-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="9b6e5-110">Çalışma zamanı çağrılabilir sarmalayıcılar</span><span class="sxs-lookup"><span data-stu-id="9b6e5-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="9b6e5-111">COM birlikte çalışma için .NET türlerini nitelendirme</span><span class="sxs-lookup"><span data-stu-id="9b6e5-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
