---
title: DotNet Listele başvuru komutu
description: Dotnet listesi başvuru komut listesi projeden projeye başvurular için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421837"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet list reference` -Projeden projeye başvurular listelenmektedir.

## <a name="synopsis"></a>Synopsis

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet list reference` Komut listesi proje başvurularını belirtilen proje veya çözüm için uygun bir seçenek sağlar.

## <a name="arguments"></a>Arguments

* **`PROJECT | SOLUTION`**

  Başvuruları listelemek için kullanılacak proje veya çözüm dosyasını belirtir. Belirtilmezse, komut, bir proje dosyasını geçerli dizinde arar.

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
