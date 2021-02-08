---
description: "Hakkında daha fazla bilgi edinin: BC30617: ' Module ' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
title: "'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: f5c3ea0cd1c08fb0243043ae50e707e2c59b00f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795787"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="00232-103">BC30617: ' Module ' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="00232-103">BC30617: 'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="00232-104">`Module` deyimler, kaynak dosyanızın en üstünde `Option` ve `Imports` deyimleri, genel öznitelikleri ve ad alanı bildirimlerinden önce, diğer tüm bildirimlerden önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="00232-104">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>

 <span data-ttu-id="00232-105">**Hata kimliği:** BC30617</span><span class="sxs-lookup"><span data-stu-id="00232-105">**Error ID:** BC30617</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="00232-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="00232-106">To correct this error</span></span>

- <span data-ttu-id="00232-107">`Module`İfadeyi ad alanı bildiriminin veya kaynak dosyanın en üstüne taşıyın.</span><span class="sxs-lookup"><span data-stu-id="00232-107">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>

## <a name="see-also"></a><span data-ttu-id="00232-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00232-108">See also</span></span>

- [<span data-ttu-id="00232-109">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="00232-109">Module Statement</span></span>](../statements/module-statement.md)
