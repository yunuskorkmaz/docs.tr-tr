---
title: DotNet Listele başvuru komutu
description: Dotnet listesi başvuru komut listesi projeden projeye başvurular için uygun bir seçenek sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665058"
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