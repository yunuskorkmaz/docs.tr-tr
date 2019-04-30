---
title: DotNet Paketi komutu Kaldır
description: Dotnet remove paket komutu bir proje için NuGet paket başvuruyu kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 05/29/2018
ms.openlocfilehash: 4cc8ac927b761547dc5e53be9abeba827bf1e1d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664863"
---
# <a name="dotnet-remove-package"></a>DotNet Kaldır paket

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet remove package` -Paket başvurusu proje dosyasından kaldırır.

## <a name="synopsis"></a>Synopsis

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet remove package` Komutu bir projeden NuGet paketi başvuruyu kaldırmak için kullanışlı bir seçenek sağlar.

## <a name="arguments"></a>Arguments

`PROJECT`

Proje dosyasını belirtir. Belirtilmezse, komut için geçerli dizinde arar.

`PACKAGE_NAME`

Kaldırmak için paket başvurusu.

## <a name="options"></a>Seçenekler

`-h|--help`

Komut için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Kaldırır `Newtonsoft.Json` geçerli dizindeki bir projeden NuGet paketi:

`dotnet remove package Newtonsoft.Json`