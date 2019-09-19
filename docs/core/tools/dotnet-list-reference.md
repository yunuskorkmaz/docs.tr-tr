---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117670"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet list reference`-Projeden projeye başvuruları listeler.

## <a name="synopsis"></a>Özeti

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Açıklama

Komut `dotnet list reference` , belirli bir proje veya çözümün proje başvurularını listelemek için uygun bir seçenek sağlar.

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
