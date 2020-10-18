---
title: "'Module' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: b946a527d3de3a030ac03691c77afcf440f518ee
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160320"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a>BC30617: ' Module ' deyimleri yalnızca dosya veya ad alanı düzeyinde bulunabilir

`Module` deyimler, kaynak dosyanızın en üstünde `Option` ve `Imports` deyimleri, genel öznitelikleri ve ad alanı bildirimlerinden önce, diğer tüm bildirimlerden önce gelmelidir.

 **Hata kimliği:** BC30617

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Module`İfadeyi ad alanı bildiriminin veya kaynak dosyanın en üstüne taşıyın.

## <a name="see-also"></a>Ayrıca bkz.

- [Module Deyimi](../statements/module-statement.md)
