---
title: -alt sistem versiyonu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802037"
---
# <a name="-subsystemversion-c-compiler-options"></a>-alt sistem versiyonu (C# Derleyici Seçenekleri)

Oluşturulan yürütülebilir dosyanın çalıştırılabildiği alt sistemin minimum sürümünü belirtir ve bu nedenle yürütülebilir dosyanın çalıştırılabildiği Windows sürümlerini belirler. En yaygın olarak, bu seçenek, yürütülebilir dosyanın Windows'un eski sürümlerinde kullanılamayan belirli güvenlik özelliklerinden yararlanmasını sağlar.

> [!NOTE]
> Alt sistemin kendisini belirtmek için [-hedef](./target-compiler-option.md) derleyici seçeneğini kullanın.

## <a name="syntax"></a>Sözdizimi

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametreler

`major.minor`

Alt sistemin, büyük ve küçük sürümler için nokta gösteriminde ifade edilen minimum gerekli sürümü. Örneğin, bu seçeneğin değerini 6.01 olarak ayarlarsanız, bu konunun daha sonra açıkladığı gibi, bir uygulamanın Windows 7'den eski bir işletim sisteminde çalıştırılamamasını belirtebilirsiniz. Ve tümseler `major` `minor` olarak değerleri belirtmeniz gerekir.

`minor` Sürümdeki satır aralığı sıfırlar sürümü değiştirmez, ancak sondaki sıfırlar değiştirir. Örneğin, 6.1 ve 6.01 aynı sürüme atıfta bulunur, ancak 6.10 farklı bir sürüme başvurur. Karışıklığı önlemek için küçük sürümü iki basamak olarak ifade etmenizi öneririz.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tabloda Windows'un ortak alt sistem sürümleri listelenmiştir.

|Windows sürümü|Alt sistem sürümü|
|---------------------|-----------------------|
|Windows 2000|5,00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Varsayılan değerler

**-subsystemversion** derleyici seçeneğinin varsayılan değeri aşağıdaki listedeki koşullara bağlıdır:

- Aşağıdaki listedeki herhangi bir derleyici seçeneği ayarlanmışsa varsayılan değer 6,02'dir:

  - [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [-target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-platform:kol](./platform-compiler-option.md)

- MSBuild kullanıyorsanız, .NET Framework 4.5'i hedefliyorsanız ve bu listede daha önce belirtilen derleyici seçeneklerinden hiçbirini ayarlamamışsanız varsayılan değer 6,00'dır.

- Önceki koşullardan hiçbiri doğru değilse varsayılan değer 4,00'dir.

## <a name="setting-this-option"></a>Bu seçeneği ayarlama

Visual Studio'da **-subsystemversion** derleyici seçeneğini ayarlamak için .csproj dosyasını açmanız ve MSBuild XML'deki `SubsystemVersion` özellik için bir değer belirtmeniz gerekir. Bu seçeneği Visual Studio IDE'de ayarlayamam. Daha fazla bilgi için, bu konu veya [Ortak MSBuild Project Özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)daha önce "Varsayılan değerler" bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
