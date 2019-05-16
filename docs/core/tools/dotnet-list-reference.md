---
title: DotNet Listele başvuru komutu
description: Dotnet listesi başvuru komut listesi projeden projeye başvurular için uygun bir seçenek sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: c0b88c4a0af4469d7ddc9e0a9368bb1b2d9d20b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632404"
---
# <a name="dotnet-list-reference"></a>DotNet listesi başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet list reference` -Projeden projeye başvurular listelenmektedir.

## <a name="synopsis"></a>Synopsis

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet list reference` Komut listesi proje başvurularını belirtilen proje veya çözüm için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Başvuruları listelemek için kullanılacak proje dosyasını belirtir. Belirtilmezse, komut, bir proje dosyasını geçerli dizinde arar.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

* Belirtilen proje için proje başvuruları listeleyin:

  ```console
  dotnet list app/app.csproj reference
  ```

* Geçerli dizinde proje için proje başvuruları listeleyin:

  ```console
  dotnet list reference
  ```
