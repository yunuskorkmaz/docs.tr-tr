---
title: 'NETSDK1004: varlıklar dosyası bulunamadı'
description: project.assets.jsdosya bulunamadığında oluşan .NET SDK hatası NETSDK1004 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 01/26/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: ed42ad0e8ebef7362cc029125fe51d3f300acbae
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98900362"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="bbb98-103">NETSDK1004: varlıklar dosyası bulunamadı</span><span class="sxs-lookup"><span data-stu-id="bbb98-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="bbb98-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="bbb98-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="bbb98-105">Bu hata, derleme sırasında *project.assets.js* varlıklar dosyası bulunamadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="bbb98-105">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="bbb98-106">Tam hata iletisi şuna benzerdir:</span><span class="sxs-lookup"><span data-stu-id="bbb98-106">The full error message is similar to:</span></span>

<span data-ttu-id="bbb98-107">**NETSDK1004: ' C:\IncorrectPath\project.assets.json ' varlık dosyası bulunamadı. Bu dosyayı oluşturmak için bir NuGet paketi geri yükleme çalıştırın.**</span><span class="sxs-lookup"><span data-stu-id="bbb98-107">**NETSDK1004: Assets file 'C:\IncorrectPath\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="bbb98-108">`dotnet build`Komutu bir karakter içeren bir dizin yolundan çalıştırırsanız, uyarı NETSDK1004 ile karşılaşabilirsiniz `%` .</span><span class="sxs-lookup"><span data-stu-id="bbb98-108">One reason you might encounter warning NETSDK1004 is if you run the `dotnet build` command from a directory path that contains a `%` character.</span></span>
