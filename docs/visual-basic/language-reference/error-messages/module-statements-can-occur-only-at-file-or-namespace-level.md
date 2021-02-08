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
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a>BC30617: ' Module ' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir

`Module` deyimler, kaynak dosyanızın en üstünde `Option` ve `Imports` deyimleri, genel öznitelikleri ve ad alanı bildirimlerinden önce, diğer tüm bildirimlerden önce gelmelidir.

 **Hata kimliği:** BC30617

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Module`İfadeyi ad alanı bildiriminin veya kaynak dosyanın en üstüne taşıyın.

## <a name="see-also"></a>Ayrıca bkz.

- [Module Deyimi](../statements/module-statement.md)
