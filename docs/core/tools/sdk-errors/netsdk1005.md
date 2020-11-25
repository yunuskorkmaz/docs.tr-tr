---
title: 'NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok'
description: Bir hedef eksik olan varlık dosyası sorununu çözme.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 207c8b0274c13e7af594e05cfac2a95907f85b81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717909"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="823e9-103">NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok</span><span class="sxs-lookup"><span data-stu-id="823e9-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="823e9-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="823e9-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="823e9-105">.NET SDK hatası NETSDK1005 veya NETSDK1047 hata verdiği zaman, projenin varlıklar dosyasında hedef çerçevelerinizdeki bir bilgi eksik.</span><span class="sxs-lookup"><span data-stu-id="823e9-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="823e9-106">Bu, genellikle geri yüklemenin çalıştırıldığından ve eksik hedef değerin projenizin özelliğine eklendiğinden emin olarak düzeltilebilir `TargetFrameworks` .</span><span class="sxs-lookup"><span data-stu-id="823e9-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="823e9-107">Bu hataya neden olan Visual Studio 16,8 önizlemeleri sürümleriyle kullanıldığında .NET 5 Preview 8 ' in erken Derlemeleriyle ilgili bilinen bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="823e9-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="823e9-108">Özellikle, eksik hedef `net5.0-windows7.0` veya ise `net5.0` , Visual Studio 'nun en son sürümlerine ve .NET 5 SDK 'sına güncelleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="823e9-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
