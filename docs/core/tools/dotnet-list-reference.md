---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503710"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet list reference`-projeden projeye başvuruları listeler.

## <a name="synopsis"></a>Özeti

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet list reference` komutu, belirli bir proje veya çözümün proje başvurularını listelemek için uygun bir seçenek sağlar.

## <a name="arguments"></a>Bağımsız Değişkenler

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
