---
title: Son değişiklikler, .NET Core 3,0 .NET Framework-.NET Core
description: Windows Forms ve Windows Presentation Foundation için .NET Framework son değişiklikleri .NET Core 3,0 'e listeler.
ms.date: 09/10/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292a6dbd26fe76486c62f860b7f546e20459d76c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119319"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core-30"></a><span data-ttu-id="c9efe-103">.NET Framework 'den .NET Core 3,0 'ye geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="c9efe-103">Breaking changes for migration from .NET Framework to .NET Core 3.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9efe-104">Bu makale yapım aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="c9efe-104">This article is under construction.</span></span> <span data-ttu-id="c9efe-105">Bu, .NET Core önemli değişikliklerinin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="c9efe-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="c9efe-106">.NET Core ile ilgili değişiklikler hakkında daha fazla bilgi için GitHub 'daki DotNet/docs deposundaki tek tek [değişiklikler sorunlarını](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9efe-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repo on GitHub.</span></span> 

<span data-ttu-id="c9efe-107">.NET Framework bir Windows Forms veya Windows Presentation Foundation uygulamasını .NET Core 3,0 ' e geçiriyorsanız, uygulamanızı etkileyebilecek değişiklikler için aşağıdaki konuları gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="c9efe-107">If you are migrating a Windows Forms or Windows Presentation Foundation application from .NET Framework to .NET Core 3.0, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="windows-forms"></a><span data-ttu-id="c9efe-108">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c9efe-108">Windows Forms</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]
