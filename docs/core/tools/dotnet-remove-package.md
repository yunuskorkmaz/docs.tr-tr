---
title: "DotNet Paketi komutu - .NET Core CLI Kaldır"
description: "Dotnet Kaldır Paketi komutu NuGet paketi başvurusu projeye kaldırmak için uygun bir seçeneği sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1bc8d9cdc4db1f103b73116b43e630185a2c35de
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-package"></a>DotNet Kaldır paketi

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet remove package`-Paket başvuru proje dosyasından kaldırır.

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
