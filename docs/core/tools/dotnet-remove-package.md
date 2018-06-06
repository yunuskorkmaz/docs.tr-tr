---
title: DotNet Paketi komutu - .NET Core CLI Kaldır
description: Dotnet Kaldır Paketi komutu NuGet paketi başvurusu projeye kaldırmak için uygun bir seçeneği sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ed6086bfdfadaa06494c857fc74687f1273af971
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696864"
---
# <a name="dotnet-remove-package"></a>DotNet Kaldır paketi

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet remove package` -Paket başvuru proje dosyasından kaldırır.

## <a name="synopsis"></a>Özet

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet remove package` Komutu bir NuGet paketi başvurusu projeden kaldırmak için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Proje dosyası belirtir. Belirtilmezse, komut için geçerli dizin arar.

`PACKAGE_NAME`

Kaldırılacak paket başvuru.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Kaldırır `Newtonsoft.Json` geçerli dizinde bir projeden NuGet paketi:

`dotnet remove package Newtonsoft.Json`