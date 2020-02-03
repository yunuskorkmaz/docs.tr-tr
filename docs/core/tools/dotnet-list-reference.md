---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733227"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet list reference`-projeden projeye başvuruları listeler.

## <a name="synopsis"></a>Özeti

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet list reference` komutu, belirli bir proje veya çözümün proje başvurularını listelemek için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

* **`PROJECT | SOLUTION`**

  Başvuruları listelemek için kullanılacak proje veya çözüm dosyasını belirtir. Belirtilmemişse, komut geçerli dizinde bir proje dosyası arar.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

* Belirtilen proje için proje başvurularını listeleyin:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Geçerli dizindeki projenin proje başvurularını listeleyin:

  ```dotnetcli
  dotnet list reference
  ```
